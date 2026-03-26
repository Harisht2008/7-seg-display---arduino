# 7-seg display - arduino
7-seg display with button debouncer
-used binary pattern
-used button debouncer
-used UART communication for debugging and testing
-created sequence for values
-could be optimized with: 
-binary search and functions (wasn't working properly during testing).
-could use less wires/ outputs.
-could add more comments for readability

Images:
![IMG_3757](https://github.com/user-attachments/assets/fe1ad925-6d8a-4357-93bd-711a7f62edb5)
![IMG_3756](https://github.com/user-attachments/assets/4b2673ce-9869-4b82-ba29-cc4ae02e1eea)
![IMG_3755](https://github.com/user-attachments/assets/7f04f41f-542e-4f67-a559-dfe95c4dd7df)
![IMG_3754](https://github.com/user-attachments/assets/9d3f9474-17af-4a75-b895-4d46959cfda3)


int pressed;
int lastReading = LOW;
unsigned long lastDebounce = 0;
unsigned long debounceDelay = 50;

void setup() {
pinMode(2,OUTPUT); // a
pinMode(3,OUTPUT); // b
pinMode(4,OUTPUT); // c
pinMode(5,OUTPUT); // d
pinMode(6,OUTPUT); // e
pinMode(7,OUTPUT); // f
pinMode(8,OUTPUT); // g
pinMode(9,INPUT); 
pinMode(10,OUTPUT);
Serial.begin(9600);
}




void loop() {
  int reading = digitalRead(9);

  digitalWrite(10,HIGH);

  if(reading != lastReading) {
    lastDebounce = millis();
  }


  if((millis() - lastDebounce) > debounceDelay) {

    if (digitalRead(9) == HIGH) {
      pressed++;
      Serial.print("Press Count:");
      Serial.println(pressed);
    }
    if (pressed == 10) {
      pressed = 0;
    }
    if (pressed == 0) {// 0: 2/3/4/5/6/7
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);

      digitalWrite(2,HIGH);
      digitalWrite(3,HIGH);
      digitalWrite(4,HIGH);
      digitalWrite(5,HIGH);
      digitalWrite(6,HIGH);
      digitalWrite(7,HIGH);
    }
    if (pressed == 1) {// 1: 3/4
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);

      digitalWrite(3,HIGH);
      digitalWrite(4,HIGH);
    }
    if (pressed == 2) {// 2: 2/3/5/6/8
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);

      digitalWrite(2,HIGH);
      digitalWrite(3,HIGH);
      digitalWrite(5,HIGH);
      digitalWrite(6,HIGH);
      digitalWrite(8,HIGH);
    }      
    if (pressed == 3) {// 3: 2/3/4/5/8
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);

      digitalWrite(2,HIGH);
      digitalWrite(3,HIGH);
      digitalWrite(4,HIGH);
      digitalWrite(5,HIGH);
      digitalWrite(8,HIGH);
    }
    if (pressed == 4) {// 4: 3/4/7/8
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);

      digitalWrite(3,HIGH);
      digitalWrite(4,HIGH);
      digitalWrite(7,HIGH);
      digitalWrite(8,HIGH);
    }
    if (pressed == 5) {// 5: 2/4/5/7/8
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);

      digitalWrite(2,HIGH);
      digitalWrite(4,HIGH);
      digitalWrite(5,HIGH);
      digitalWrite(7,HIGH);
      digitalWrite(8,HIGH);
    }
    if (pressed == 6) {// 6: 2/4/5/6/7/8
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);

      digitalWrite(2,HIGH);
      digitalWrite(4,HIGH);
      digitalWrite(5,HIGH);
      digitalWrite(6,HIGH);
      digitalWrite(7,HIGH);
      digitalWrite(8,HIGH);
    }
    if (pressed == 7) {// 7: 2/3/4
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);

      digitalWrite(2,HIGH);
      digitalWrite(3,HIGH);
      digitalWrite(4,HIGH);
    }
    if (pressed == 8) {// 8: 2/3/4/5/6/7/8
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);

      digitalWrite(2,HIGH);
      digitalWrite(3,HIGH);
      digitalWrite(4,HIGH);
      digitalWrite(5,HIGH);
      digitalWrite(6,HIGH);
      digitalWrite(7,HIGH);
      digitalWrite(8,HIGH);
    }
    if (pressed == 9) {// 9: 2/3/4/5/7/8
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);

      digitalWrite(2,HIGH);
      digitalWrite(3,HIGH);
      digitalWrite(4,HIGH);
      digitalWrite(5,HIGH);
      digitalWrite(7,HIGH);
      digitalWrite(8,HIGH);
    }
    if (pressed == 10) {// 9: 2/3/4/5/7/8
      digitalWrite(2,LOW);
      digitalWrite(3,LOW);
      digitalWrite(4,LOW);
      digitalWrite(5,LOW);
      digitalWrite(6,LOW);
      digitalWrite(7,LOW);
      digitalWrite(8,LOW);
    }  
  }
}
