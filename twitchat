import socket


class Twitchat:
    irc = socket.socket()

    def __init__(self, username, password, channel):
        self.irc = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        self.username = username
        self.password = password
        self.channel = channel

    def send(self, msg):
        self.irc.send(("PRIVMSG " + self.channel + " " + msg + "n").encode("utf-8"))

    def connect(self):
        print("connecting to channel: " + self.channel)
        self.irc.connect(("irc.twitch.tv", 6667))
        self.irc.send(("PASS " + self.password + "\r\n").encode("utf-8"))
        self.irc.send(("NICK " + self.username + "\r\n").encode("utf-8"))
        self.irc.send(("JOIN #" + self.channel + "\r\n").encode("utf-8"))

    def get_text(self):
        text = (self.irc.recv(1024)).decode("utf-8")  # receive the text

        if text.find('PING') != -1:
            self.irc.send(('PONG ' + text.split()[1] + '\r\n').encode("utf-8"))
        return text

    def get_message(self):
        text = (self.irc.recv(1024)).decode("utf-8")
        if text.find("PRIVMSG") != -1:
            msgusr = text.split("!")[0]
            msgusr = msgusr[1:]
            tempmessage = text.split("PRIVMSG #" + self.channel + " :")[1]
            content = tempmessage[:-2]
            msg = msgusr + ": " + content

            return msg
