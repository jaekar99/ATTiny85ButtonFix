# ATTiny85ButtonFix
A fix for the Adafruit button cycler fix

I loaded the correction code into the Adafruit Button Cycler sketch:

//************************************************************
void loop() 
{
   // Get current button state.
   bool newState = digitalRead(BUTTON_PIN);

   // Check if state changed from high to low (button press).
   if (newState == LOW && oldState == HIGH) 
   {
      // Short delay to debounce button.
      delay(20);
      // Check if button is still low after debounce.
      newState = digitalRead(BUTTON_PIN);
      if (newState == LOW) 
      {
         showType++;
         if (showType > 9)
         showType=0;
         startShow(showType);
      }
   }
   startShow(showType);

   // Set the last button state to the old state.
   oldState = newState;
}
//*************************************************************


Streamlined to work on an ATTiny85
