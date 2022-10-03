### Introduction
___________________________________________________________________________________________________

This course will provide a short introduction into the world of communication and how different
devices can exchange information. 

- communication, network, protocol
- medium, voltage, duration encoding, amplitude encoding
- simplex, semiduplex, duplex
- binary system, bit, byte, encoding, ASCII
- RS-232, Ethernet, IP, TCP, UDP, DHCP, DNS
- OSI Model, ARPA Model
- Internet protocols

### Let there be light ...
___________________________________________________________________________________________________


TODO: Place a picture

Let's start with an example of a very simple communication between two ships. The ships has a 
captain and a communication officer. The two ships are 5 km away and it is dark. The communicaiton
officers will use light to transmit information. 

Now the captain of ship A wants to transmit the message 'Hi' to the other ship. He goes to the 
communication officer to give the information to be transmitted. The communication officer has a
set of rules: for H he will use 4 short pulses of light, for I two short pulses. Now he uses light
to transmit the message. This is called encoding through duration and it is the well known morse code.
The encoding process determines how to manipulate the medium (light) to transmit information (pulses). 

The other ships sees the light and the communication officer starts recording. He sees 4 short 
impulses and checks his table. It says 'H'. Then after a pause he sees two short impulses, 
which according to his rules table is 'I'. As there is not other information transmitted from 
ship A, he will deliver the recorded message to his captain. And voiala, we have transmitted a
message between the two ships.

In our example we can identify four crucial part of a communicatin system:

- A medium to transmit information (light)
- A set of rules used by both sides (protocol)
- Someone who transmits the information (officer)
- Someone who talks (captain)

Ways of communication

- Show a simplex circuit (traffic light, TV)
- Show a semiduplex circuit (talking)
- Show a duplex circuit (morse code)


### Telegraph: from light to volt
___________________________________________________________________________________________________

The lenght of a dot is one unit: dit

The same points can be generalised for other types of communication, for example between two 
computers. The only difference will be the medium and the terms we use to describe the parts of
the system...

- A medium to transmit information (voltage)
- A set of rules used by both sides (protocol)
- Something which transmits the information (transmitter)
- Something which talks (node)

TODO: Picture

TODO: Picture, workshop with resistors

Now, let's define what is low voltage and what high voltage. For our example we will use 0 for 
low and 5 for high. The second thing is to think about how to transmit and receive using voltage. 

keywords: voltage, resistor, ground, duplex, problems with separate GNDs, definition of voltage zones.

Ask ourselves how we know if the line is cut or the pause is deliberate while using the telegraph?

To mitigate this problem we will invert the logic. The line will always have voltage and will be
interrupted to send short or long pulses.

The electrical telegraph can now detect problems on the line. But for two parties to communicate
they must know when a message has finished. The problem can be solved by using a standard duration
after which the line is considered free or a special code which indicates the end of message
transmission (prosign). They can also be used in case the operator couldn't write down the message
and ask for retransmission.

Now we can transmit info, say it is over and check if the line is interrupted.

Workshop: 

- Demonstrate the telegraph with a simple circuit involving resistors and diodes


### RS-232: Pack the data
___________________________________________________________________________________________________

The problem with the telegraph is that it uses a lot of pauses. For every pulse transmitted there
is a small pause. Remember, that there is space between pulses in letters, spaces between letters
and spaces between words. This reduces greatly the efficiency of the morse code greatly.

Now let's use a trick and assign numbers to the pulse durations. For us the short pulse
will be 0 and the long pulse will be 1. In our new scenario we don't have a pause, because we want
to compress the information as much as possible.

The code now is a little bit more readable. But it has another advantage too as the binary system 
can be easily used by any kind electronic devices. Zero means simply low voltage and one means 
high voltage and this simplicity simplifies the construction of digital devices. For example a 
memory component can be implemented using a capacitor. If it is empty we have 0, if it is charged
it is 1/ One interesting fact here is that John Atanasoff had the idea to apply the binary system 
and thus basically laying ground for all the modern digitial devices we all know.

Now let's transform the morse code using 0s and 1s. So, we have now the morse code writeen in the
binary system. What we notice regarding this code? It is a so called variable encoding. The most
used symbols are encoded with less pulses. This is indeed very nice, but how we are supposed now
to know when the tranmission ends?

Very simple: Always transmit the same amount of information. Now in digital systems using the
binary system a single 0 or 1 is called a bit. Now when we check the morse code we will see that
the longest code is for the numbers and they will use 5 bits.

The morse code though uses only capital letters and doesn't have any special symbols. In modern
age we need %, $ and we might even think to encode directly some procedures such as end-of-line
of end-of-transmission. This type of encoding is called ASCII encoding. It uses a fixed amount of
bits and can encode up to 256 characters. Reading the wiki page we can see that the ASCII code
is related to the telegraph code. 

Based on the information above we will develop a simple protocol which:

- will have a low (-5) and high voltage(+5)
- will have and idle state set to high
- will have and indication if the line is cut (voltage is 0)
- will indicate transmission by exiting the idle state for a fixed amount of time
- will transmit 8 bits whereby each bit duration is fixed
- will return and stay in idle for a fixed amount of time

TODO: Plot Rx, Tx lines and the cross-over connection. Show similarity with the telegraph.

We see that electrically we didn't change that much, we just change how signals are transmitted
over the electrical line.

Mention baudrate (brutto bits/s), bitrate (netto bits/s).

Bonus: Talk a little bit about parity bits and control flow
Workshop: Two laptops with RS-232 and communication configuration



### Client/Server: Who is who?
___________________________________________________________________________________________________

- Draw Tx/Rx lines and connect them at random, show logical bus and physical daisy-chain topologies
- Improve readability by drawing a nice and organized network with two shared lines Tx and Rx
- Add voltage and GND
- Add termination resistor and explain why we need them (reflection, antenna)
- Master/Slave examples (PLC, sensors) with old names, client/server with new names
- Only master/client asks, slave/server responds, usage of addresses
- SPI, IIC, Modbus, etc.
- Example of a half-duplex communication with multiple partners
- Show importance of addresses

### Topologies
___________________________________________________________________________________________________

Start with an example travelling from Varna to Sofia. We have to pass through each city and if
the city is closed, bam. Then we will make a second route passing through other cities and ending
again in Sofia (ring). Now we want to save some money and allow each city to be connected to other
cities using star topology. 

Varna - Nesebar - Burgas



### Ethernet
___________________________________________________________________________________________________

RS-485 with master/slave is actually quite good, it has reach but it is still quite unefficient as
it works in a half-duplex mode. There can be only one active requesting device on the line. How to
improve this? 

The next step is to allow devices to talk all at the same time. This is 
called a broadcast communication. The Ethernet standard, which is now part of the internet protocols
is doing exactly this. But what if two devices start to talk over each other? Well, we have the 
collision detection mechanism. 

Together: CSMA/CD

TODO: Explain a little bit more elabortate how it work with pictures...
TODO: Bus 


### Internet protocol
___________________________________________________________________________________________________


### Transport protocols
___________________________________________________________________________________________________


### Other protocols
___________________________________________________________________________________________________


### Protocol classification
___________________________________________________________________________________________________


### Operating system and protocols
___________________________________________________________________________________________________


### Glossary
