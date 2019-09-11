# twitchat
An easy to use Twitch IRC client which monitors and send to twitch chat coded in pyhton

## use it
1. download the file and put it in your directory where your script is
2. import it with `from twitchat import Twitchat`
3. when creating an Twitchat object, it needs the username, password and the channel. The password is the oauth-Token

## doc
`connect()`
That function simply connects to a channel which is given in the initialization of the class.

`get_message()`
waits for a message on the channel given in the initialization of the class. You can loop it to completly mirror it.

`send(msg)`
send a message which has to be defined in the funtion call to the channel given in the initialization.

`get_text()`
outdated function of the get message. It will give you an unparsed IRC message which is not very readable. Use it for debugging.

## example
Here is a little code example for you:
```
from irc import Twitchat
import time

username = "c9sneaky"
password = "oauth:asdfjklö12347890"
channel = "r4nd0wn"

chat = Twitchat(username, password, channel)
chat.connect
while True:
  print(get_message())
  time.sleep(0.2) #optional
