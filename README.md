# arduino-threading
a library for threading with arduino
how it works is you make aa function representing the thread.
now create a instance of a thread passing as parameters the delay time you want the thread to run in( how many miliseconds will pass before it will execute the function again), and the name of the function representing the thread.
now all you need to do is call the work function on the instance of the thread inside the loop.
example:

bool red = false;
void redBlink()
{
  digitalWrite(13, red);
  red = !red;
}
bool green = false;
void greenBlink()
{
  digitalWrite(12, green);
  green = !green;
}
Thread redThread(1000, redBlink);
Thread greenThread(500, greenBlink);
void setup()
{
  pinMode(13, 1);//13 is the pin connected to the red led
  pinMode(12, 1);//12 "   "   "      "      "   "  green led
}
void loop()
{
  redThread.work();
  greenThread.work();
}
