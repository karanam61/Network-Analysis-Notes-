![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image1.png)

I've been given a pcap file for analysis . Lets solve it as a ctf .

![A blue and white rectangle with text AI-generated content may be
incorrect.](media1/media/image2.png)

To answer this question firstly I've filtered out the smtp traffic using
the smtp filter .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image3.png)

Now we will try to analyze each packet in fast forward .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image4.png)

Cliché name but I think we found the email .

![A blue and black rectangular object AI-generated content may be
incorrect.](media1/media/image5.png)

To answerthis question I need to go to the packet where authentication
takes place .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image6.png)

From here on I will right click on the packet and follow the Tcp stream.

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image7.png)

I can see hex encoding so IF I decode it I got the password written in
the answer above

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image8.png)

To answer I must the check the packet where an email transaction
actually took place.

![A screenshot of a computer code AI-generated content may be
incorrect.](media1/media/image9.png)

When I followed along the Tcp stream I found this .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image10.png)

To analyze the content of the docx we can dump the entire encoded text
into cyberchef to get meaningful results .
