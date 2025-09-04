![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image1.png){width="6.5in" height="3.29375in"}

I've been given a pcap file for analysis . Lets solve it as a ctf .

![A blue and white rectangle with text AI-generated content may be
incorrect.](media1/media/image2.png){width="6.5in"
height="1.4090277777777778in"}

To answer this question firstly I've filtered out the smtp traffic using
the smtp filter .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image3.png){width="6.5in"
height="3.261111111111111in"}

Now we will try to analyze each packet in fast forward .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image4.png){width="6.5in"
height="3.9604166666666667in"}

Cliché name but I think we found the email .

![A blue and black rectangular object AI-generated content may be
incorrect.](media1/media/image5.png){width="6.5in"
height="1.5152777777777777in"}

To answerthis question I need to go to the packet where authentication
takes place .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image6.png){width="6.5in"
height="4.246527777777778in"}

From here on I will right click on the packet and follow the Tcp stream.

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image7.png){width="6.5in"
height="4.9631944444444445in"}

I can see hex encoding so IF I decode it I got the password written in
the answer above

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image8.png){width="6.5in"
height="1.2409722222222221in"}

To answer I must the check the packet where an email transaction
actually took place.

![A screenshot of a computer code AI-generated content may be
incorrect.](media1/media/image9.png){width="6.5in"
height="4.952083333333333in"}

When I followed along the Tcp stream I found this .

![A screenshot of a computer AI-generated content may be
incorrect.](media1/media/image10.png){width="6.5in"
height="1.2430555555555556in"}

To analyze the content of the docx we can dump the entire encoded text
into cyberchef to get meaningful results .
