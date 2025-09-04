Brute force attack .

# I've been given both pcap aswell as an authentication log to analyze a brute force attack.

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media1/media/media2/media/image1.png)

Up until log no 122 I can see a user with Ip 196.136.60.15 having
multiple authentication sessions to the root user .

But then I see multiple authentication failures from an Ip 141.98.10.105
, An unsual amounts of time that the session gets closed . Don't see
anything suspicious on network logs so its probably an internal Ip .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image2.png)

And parallely in network logs the IP 192.168.190.137 is attempting for
an RDP to 51.116.96.181 multiple times aswell so we will look for the
same ip in the auth logs.

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image3.png)

Also see that its successful as packets are being exchanged so the
server compromised here is definitely 51.116.96.181 .

![A screen shot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image4.png)

![A blue and white rectangle with white text AI-generated content may be
incorrect.](media1/media/media2/media/image5.png)

To answer this question we filter the wireshark for http requests as it
is the only way to target a specific server directory .

Let us check whats going on .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image6.png)

Multiple post requests to the directory index.php so probably its
targeting that to authenticate .

We can confirm it through the http/1.1 request that

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image7.png)

Just to confirm . Used statistics + http as well as statistics end
points .

![A blue and white rectangle with white text AI-generated content may be
incorrect.](media1/media/media2/media/image8.png)

To answer this question we need to analyze the HTTP/POST

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image9.png)

Confirms that its actually posting a series of username and password .

Now whether its correct or wrong can be seen in the response .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image10.png)

For every wrong combination we get the incorrect response in red . For
the correct one the response would be correct right ?

I didn't know how to apply a filter for text like this . I used external
help and found out that .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image11.png)

This is how we do it is what I've learnt .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image12.png)

So the post request before this would have the correct username and
password combination .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image13.png

![A blue and white text AI-generated content may be
incorrect.](media1/media/media2/media/image14.png)

We've got the right combination .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image15.png)

Its basically the no of attempted password logins for different
usernames so we need to segregate out the post request by applying a
filter like this .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image16.png)

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image17.png)

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image18.png)

We'll just export it outside and use some linux commands .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image19.png)

We get 7 unique usernames .

![A blue and white text AI-generated content may be
incorrect.](media1/media/media2/media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image21.png)

To find anything from a request or anything other than the given fields
we will search it using the the second filter .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image22.png)

![A blue and white screen AI-generated content may be
incorrect.](media1/media/media2/media/image23.png)

For the next question

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image24.png)

![A blue and white rectangle with white text AI-generated content may be
incorrect.](media1/media/media2/media/image25.png)

![A blue and white text AI-generated content may be
incorrect.](media1/media/media2/media/image26.png)

As he asked for the latest so we scrolled through to find the answer .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image27.png)

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image28.png)

![A blue background with white text AI-generated content may be
incorrect.](media1/media/media2/media/image29.png)

![A blue line in a dark background AI-generated content may be
incorrect.](media1/media/media2/media/image30.png)

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/media2/media/image31.png)

Clearly it's a brute force so we'll find the mitre id for it .

![A blue rectangular object with a black stripe AI-generated content may
be incorrect.](media1/media/media2/media/image32.png)
