from tweepy.streaming import StreamListener
from tweepy import OAuthHandler
from tweepy import Stream

access_token = "1145809453-ctTAQZdvp4E6lFlyuFxU21Ke01cxfr3niEz1VB5"
access_token_secret = "XEfQKspCOz47X1cC1DzBAXKHynLjdV1hlP3KyjaaBA6Vt"
consumer_key = "REMK0Pi0Ioz6hhlTp0o9AMCss"
consumer_secret = "jEXf0OzqGL8ah7YwQ2f5dgE6OA438mXND74vquVOyoI0CkWWl8"


class listener(StreamListener):

    def on_data(self, data):
        try:
            with open('tweets_pdb1.json','a') as f:
                f.write(data)
                return True
        except BaseException as e:
            print("error on data: %s" %str(e))
            return Trues

    def on_error(self, status):
        print status

auth = OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)
twitterStream = Stream(auth,listener())
twitterStream.filter(track=["entertainment","politics","environment","education","business"]) 
# git_repo
