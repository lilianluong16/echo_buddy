# Word Buddy Alexa Skill

Word Buddy is an Alexa skill that solves analogies 

## Required modules:

Install these modules before attempting to run FriendBuddy:

 * pickle
 * numpy
 * [glove](https://www.dropbox.com/s/c6m006wzrzb2p6t/glove.6B.50d.txt.w2v.zip?dl=0) (download into the word buddy folder)
 * [ngrok](https://ngrok.com/ "ngrok information and download page")
 * [Flask-ask](https://flask-ask.readthedocs.io/en/latest/ "Flask-ask information and download page")

## Setup

Enter the [Alexa Skills Kit](https://developer.amazon.com/edw/home.html#/skills "Amazon's Alexa Skills Kit"), which requires an Amazon developer account.

Add a new skill using the button in the upper right corner.

Enter "WordBuddy" as the name and "word buddy" as the invocation name. Click the next button in the bottom right corner to proceed to the Interaction Model.

Paste the following into the Intent Schema section in the Interaction Model:
    
  ```
 {
  "intents": [
    {
      "slots": [
        {
          "name": "thatone",
          "type": "AMAZON.LITERAL"
        },
        {
          "name": "thistwo",
          "type": "AMAZON.LITERAL"
        },
        {
          "name": "thattwo",
          "type": "AMAZON.LITERAL"
        }
      ],
      "intent": "ThisIntent"
    },
    {
      "slots": [
        {
          "name": "thisone",
          "type": "AMAZON.LITERAL"
        },
        {
          "name": "thistwo",
          "type": "AMAZON.LITERAL"
        },
        {
          "name": "thattwo",
          "type": "AMAZON.LITERAL"
        }
      ],
      "intent": "ThatIntent"
    },
    {
      "slots": [
        {
          "name": "word",
          "type": "AMAZON.LITERAL"
        }
      ],
      "intent": "WordIntent"
    }
  ]
}
  ```
  
  And paste the following into Sample Utterances section in the Interaction Model:
  ```
ThisIntent {man|thistwo} is to {boy|thattwo} as what is to {girl|thatone}
ThisIntent {honest|thistwo} is to {dishonest|thattwo} as blank is to {never|thatone}
ThisIntent {large|thistwo} is to {small|thattwo} as this is to {big|thatone}
ThisIntent what is to {dog|thatone} as {cat|thistwo} is to {kitten|thattwo}
ThisIntent this is to {bad|thatone} as {better|thistwo} is to {good|thattwo}
ThisIntent blank is to {queen|thatone} as {man|thistwo} is to {king|thattwo}
ThisIntent solve the analogy {high|thistwo} is to {low|thattwo} as blank is to {bad|thatone}
ThisIntent solve the analogy {sad|thistwo} is to {happy|thattwo} as this is to {good|thatone}
ThisIntent solve the analogy this is to {brother|thatone} as {mother|thistwo} is to {father|thattwo}
ThisIntent solve the analogy blank is to {truck|thatone} as {blue|thistwo} is to {sky|thattwo}
ThatIntent what is to {boy|thisone} as {girl|thistwo} is to {daugther|thattwo}
ThatIntent blank is to {sad|thisone} as {glad|thistwo} is to {happy|thattwo}
ThatIntent this is to {intelligent|thisone} as {smart|thistwo} is to {dumb|thattwo}
ThatIntent {crying|thistwo} is to {smiling|thattwo} as {sad|thisone} is to what
ThatIntent {sunny|thistwo} is to {snowy|thattwo} as {summer|thisone} is to blank
ThatIntent {mean|thistwo} is to {kind|thattwo} as {cruel|thisone} is to this
ThatIntent solve the analogy blank is to {fire|thisone} as {cold|thistwo} is to {ice|thattwo}
ThatIntent solve the analogy this is to {firefighter|thisone} as {gun|thistwo} is to {police|thattwo}
ThatIntent solve the analogy {train|thistwo} is to {track|thattwo} as {car|thisone} is to blank
ThatIntent solve the analogy {tall|thistwo} is to {fat|thattwo} as {height|thisone} is to this
WordIntent {bugs|word}
WordIntent whats related to {school|word}
WordIntent what are some words like {yellow|word}
WordIntent related to {dog|word}
WordIntent things like {children|word}
WordIntent things related to {medicine|word}
WordIntent give me words like {fluffy|word}
WordIntent give me words similar to {magic|word}
WordIntent tell me words like {dancing|word}
WordIntent tell me things like {ran|word}
WordIntent give me words similar to {sun|word}
  ```
  
  Save the Interaction Model using the save button at the bottom of the page.
  
  Clone or download this folder. Navigate to the resulting directory.
  
  Run:
  ```
  python news_buddy.py
  ```
  
  This will start a local host at port 5010.
  
  Use [ngrok](https://ngrok.com/ "ngrok information and download page") to create a tunnel to your local host by navigating to the folder in which you installed ngrok and then running
  
  ```
  .\ngrok http 5010
  ```
  
  In the Alexa Skills Kit, click Next on the Interaction Model tab to proceed to the Configuration tab.
  
  Select HTTPS as the Endpoint, then your location as the region closest to your target customer.
  
  Copy and paste the secure-url generated by ngrok into the box under Endpoint in the Configuration tab.
  
  Save the Configuration using the save button at the bottom of the page.
  
  Your Alexa skill is now ready to run.

  
## Usage

Say "word buddy" to trigger this skill.

Ask for related words to get a list of ten related words.

Say an incompltete analogy to return the analogy completed with three possible words.
