Brute force attack .

# I've been given both pcap aswell as an authentication log to analyze a brute force attack.

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image1.png){width="6.5in"
height="3.321527777777778in"}

Up until log no 122 I can see a user with Ip 196.136.60.15 having
multiple authentication sessions to the root user .

But then I see multiple authentication failures from an Ip 141.98.10.105
, An unsual amounts of time that the session gets closed . Don't see
anything suspicious on network logs so its probably an internal Ip .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image2.png){width="6.5in"
height="2.571527777777778in"}

And parallely in network logs the IP 192.168.190.137 is attempting for
an RDP to 51.116.96.181 multiple times aswell so we will look for the
same ip in the auth logs.

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image3.png){width="6.5in"
height="3.522222222222222in"}

Also see that its successful as packets are being exchanged so the
server compromised here is definitely 51.116.96.181 .

![A screen shot of a computer AI-generated content may be
incorrect.](media2/media/image4.png){width="6.5in"
height="1.1597222222222223in"}

![A blue and white rectangle with white text AI-generated content may be
incorrect.](media2/media/image5.png){width="6.5in"
height="0.9763888888888889in"}

To answer this question we filter the wireshark for http requests as it
is the only way to target a specific server directory .

Let us check whats going on .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image6.png){width="6.5in"
height="1.6027777777777779in"}

Multiple post requests to the directory index.php so probably its
targeting that to authenticate .

We can confirm it through the http/1.1 request that

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image7.png){width="6.5in"
height="3.957638888888889in"}

Just to confirm . Used statistics + http as well as statistics end
points .

![A blue and white rectangle with white text AI-generated content may be
incorrect.](media2/media/image8.png){width="6.5in"
height="1.1715277777777777in"}

To answer this question we need to analyze the HTTP/POST

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image9.png){width="6.5in"
height="3.839583333333333in"}

Confirms that its actually posting a series of username and password .

Now whether its correct or wrong can be seen in the response .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image10.png){width="6.5in"
height="4.411111111111111in"}

For every wrong combination we get the incorrect response in red . For
the correct one the response would be correct right ?

I didn't know how to apply a filter for text like this . I used external
help and found out that .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image11.png){width="6.5in"
height="3.308333333333333in"}

This is how we do it is what I've learnt .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image12.png){width="6.5in"
height="4.209027777777778in"}

So the post request before this would have the correct username and
password combination .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image13.png){width="6.5in"
height="4.313194444444444in"}

![A blue and white text AI-generated content may be
incorrect.](media2/media/image14.png){width="6.5in"
height="1.3618055555555555in"}

We've got the right combination .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image15.png){width="6.5in"
height="1.4722222222222223in"}

Its basically the no of attempted password logins for different
usernames so we need to segregate out the post request by applying a
filter like this .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image16.png){width="6.5in"
height="2.8513888888888888in"}

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image17.png){width="6.5in"
height="4.470138888888889in"}

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image18.png){width="6.5in"
height="4.138888888888889in"}

We'll just export it outside and use some linux commands .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image19.png){width="6.5in"
height="3.9347222222222222in"}

We get 7 unique usernames .

![A blue and white text AI-generated content may be
incorrect.](media2/media/image20.png){width="6.5in"
height="1.3243055555555556in"}

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image21.png){width="6.5in"
height="4.536111111111111in"}

To find anything from a request or anything other than the given fields
we will search it using the the second filter .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image22.png){width="6.5in"
height="4.084722222222222in"}

![A blue and white screen AI-generated content may be
incorrect.](media2/media/image23.png){width="6.5in"
height="1.3965277777777778in"}

For the next question

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image24.png){width="6.5in"
height="4.611111111111111in"}

![A blue and white rectangle with white text AI-generated content may be
incorrect.](media2/media/image25.png){width="6.5in"
height="1.3347222222222221in"}

![A blue and white text AI-generated content may be
incorrect.](media2/media/image26.png){width="6.5in"
height="1.4736111111111112in"}

As he asked for the latest so we scrolled through to find the answer .

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image27.png){width="6.5in"
height="5.689583333333333in"}

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image28.png){width="6.5in"
height="1.1701388888888888in"}

![A blue background with white text AI-generated content may be
incorrect.](media2/media/image29.png){width="6.5in"
height="1.207638888888889in"}

![A blue line in a dark background AI-generated content may be
incorrect.](media2/media/image30.png){width="6.5in"
height="1.3076388888888888in"}

![A screenshot of a computer AI-generated content may be
incorrect.](media2/media/image31.png){width="6.5in"
height="2.7319444444444443in"}

Clearly it's a brute force so we'll find the mitre id for it .

![A blue rectangular object with a black stripe AI-generated content may
be incorrect.](media2/media/image32.png){width="6.5in"
height="1.7284722222222222in"}
