# Home-AutomationString inputs;

#define relay5 6 //Connect relay5 to pin 5

void setup()
{
Serial.begin(9600); //Set rate for communicating with phone

pinMode(relay5, OUTPUT); //Set relay1 as an output

digitalWrite(relay5, LOW); //Switch relay1 off

}
void loop()
{
while(Serial.available()) //Check if there are available bytes to read
{
delay(10); //Delay to make it stable
char c = Serial.read(); //Conduct a serial read
if (c == '#'){
break; //Stop the loop once # is detected after a word
}
inputs += c; //Means inputs = inputs + c
}
if (inputs.length() >0)
{
Serial.println(inputs);


if(inputs == "E")
{
digitalWrite(relay5, LOW);
}
else if(inputs == "e")
{
digitalWrite(relay5, HIGH);
}

inputs="";
}
}
