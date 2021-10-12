# AI-Chatbot-for-Suicide-Prevention

## Purpose
Our chatbot’s goal in the end, is to aid those who are in need of counselling. It serves as a chatbot that provides people with information relevant to suicide and mental disorders, and interacts with them in such a way, in order to make them feel they are talking to a human. This chatbot could in the future undergo some more fine tuning with respect to its responses.

## OUR CHATBOT VS OTHERS
While other chatbots may answer simple questions, our chatbot is linked to a mental health website from where it obtains all its information, so as to provide correct and accurate answers, and all FAQ by mental patients are addressed directly. This makes it considerably easier for people for people to ask their questions without the fear of being judged. To make the application more human-like, normal human responses are hardcoded into the chatbot.
The chatbot is programmed in python and how this chatbot works made to work is, we utilize a number of different packages like nltk, which is a language processing library in python and newspaper3k which allows us to use the information from the mental health website. 


## PROCEDURE
First, the article containing the information regarding the symptoms and causes of a particular mental disorder that is on the website in question, is first taken in its entirety and converted into its text format. This entire portion of text then undergoes tokenization, which basically means that individual sentences in the article are entered into a list. The user’s input is then taken, and the words in the query are then compared to each and every sentence in the given article. This procedure is followed as the probability that the answer to the user’s query lies in the most similar sentence is high.
Since the query might be similar to a number of sentences in the article, this means that a need for determining the most similar sentence arises. This is done through the process of formulating a similarity score list as visible from the following code block:
cm=CountVectorizer().fit_transform(sentence_list)
similarity_scores=cosine_similarity(cm[-1],cm)
similarity_scores_list=similarity_scores.flatten()
index=index_sort(similarity_scores_list)

In this method the scores that are obtained for the sentences that are similar, are made into a list and arranged in descending order by the next section of code:
```
def index_sort(list_var):
  length = len(list_var)
  list_index = list(range(0,length))

  x = list_var
  for i in range(length):
      for j in range(length):
        if x[list_index[i]] > x[list_index[j]]:        
             temp = list_index[i]
             list_index[i] = list_index[j]
             list_index[j] = temp
  return list_index          
```
if no matching sentence was found, the bot will respond with ”I apologise, I don’t understand” . If, however, a response is found, then the response with the highest similarity score will be displayed as the output to the user’s query.
There are a few responses that are hardcoded into the program, so as to make the bot seem more human and real. Now the flow for the final program will be as follows:
1.	User connects to doc bot
2.	User gives query
3.	Program checks if query has hardcoded reply first
4.	 If no hardcoded reply, then program will search article for best suited reply
5.	Program gives reply
6.	Program loops until user gives an input signaling to exit from chatbot. 

