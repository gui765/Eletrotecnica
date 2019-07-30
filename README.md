# Piano Capacitivo
# Descrição:
Este é um projeto simples usando um Arduino, um teclado desenhado usando lápis, um papel e um alto-falante.
# Materiais
Fios de ligação macho-macho
Tábua de pão
Arduino Uno
Resistor 1M ohm
Alto falante
Lápis
Papel A4
Clipe de papel
# Sensor capacitivo
O sensoriamento por toque capacitivo é um modo de detecção do toque humano, que requer pouca ou nenhuma força para ser ativado. Pode ser usado para detectar o toque humano através de mais de um quarto de polegada de plástico, madeira, cerâmica ou outro material isolante (não qualquer tipo de metal), permitindo que o sensor seja completamente visualmente oculto.
# Por que toque capacitivo?
A placa do sensor e seu corpo formam um capacitor. Sabemos que um capacitor armazena carga. Quanto mais sua capacitância, mais carga pode armazenar.
A capacitância deste sensor de toque capacitivo depende de quão perto sua mão está da placa.
# O que o Arduino faz?
Basicamente, o Arduino mede quanto tempo o capacitor (ou seja, o sensor de toque) leva para carregar, dando uma estimativa da capacitância.

A capacitância pode ser muito pequena, mas o Arduino mede com precisão.

Uma maneira de usar o toque capacitivo em um projeto é usar a biblioteca CapSense. Para a biblioteca CapSense, o arduino usa um pino de envio e qualquer número de pinos de recebimento necessários. Um pino de recepção é conectado ao pino de envio por meio de um resistor de valor médio a alto.

Aqui estão algumas diretrizes para resistores, mas experimente uma resposta desejada.

Use um resistor de 1 megohm (ou menos talvez) para toque absoluto para ativar.
Com um resistor de 10 megohm, o sensor começará a responder a 4-6 polegadas de distância.
# Código
// Importa a biblioteca CapacitiveSensor.
#include <CapacitiveSensor.h> 
#define speaker 11 // Defina o Pin de Envio e o PIN de Recebimento.
CapacitiveSensor    cs_2_3 = CapacitiveSensor ( 2 , 3 ) ; CapacitiveSensor    cs_2_4 = CapacitiveSensor ( 2 , 4 ) ; CapacitiveSensor    cs_2_5 = CapacitiveSensor ( 2 , 5 ) ; CapacitiveSensor    cs_2_6 = CapacitiveSensor ( 2 , 6 )


 



         
          
      
 ;      
CapacitiveSensor    cs_2_7  = CapacitiveSensor ( 2 , 7 ) ;       
CapacitiveSensor    cs_2_8  = CapacitiveSensor ( 2 , 8 ) ;          
CapacitiveSensor    cs_2_9  = CapacitiveSensor ( 2 , 9 ) ;   
CapacitiveSensor    cs_2_10  = CapacitiveSensor ( 2 , 10 ) ;      
void setup () {   cs_2_6.set_CS_AutocaL_Millis ( 0xFFFFFFFF ) ;


                    

     // desativa o calibração automática no canal 1 - apenas como exemplo
 
  // Arduino começa a se comunicar com o computador.
  Serial.begin ( 9600 ) ; } void loop () {   // Define um temporizador.
início   longo = millis () ;   // Define a sensibilidade dos sensores.
  long total1 =   cs_2_3.capacitiveSensor ( 3000 ) ;   long total2 =   cs_2_4.capacitiveSensor ( 3000 ) ;   longo total3 =
  



                    

 
  
 
 
   cs_2_5.capacitiveSensor(3000);
  long total4 =  cs_2_6.capacitiveSensor(3000);
  long total5 =  cs_2_7.capacitiveSensor(3000);
  long total6 =  cs_2_8.capacitiveSensor(3000);
  long total7 =  cs_2_9.capacitiveSensor(3000);
  long total8 =  cs_2_10.capacitiveSensor(3000);
  


  Serial.print(millis() - start);        // check on performance in milliseconds
  Serial.print("\t");                    // tab character for debug windown spacing

  Serial.print(total1);                  // print sensor output 1
  Serial.print("\t");                    // Leave some space before print the next output
  Serial.print(total2);                  // print sensor output 2
  Serial.print("\t");                    // Leave some space before print the next output
  Serial.print(total3);                  // print sensor output 3
  Serial.print("\t");                    // Leave some space before print the next output
  Serial.print(total4);                  // print sensor output 4
  Serial.print("\t");                    // Leave some space before print the next output
  Serial.print(total5);                  // print sensor output 5
  Serial.print("\t");                    // Leave some space before print the next output
  Serial.print(total6);                  // print sensor output 6
  Serial.print("\t");                    // Leave some space before print the next output
  Serial.print(total7);                   // print sensor output 7
                                          // Leave some space before print the next output
  Serial.print("\t");
  Serial.println(total8);                 // print sensor output 8
                                         // "println" - "ln" represent as "line", system will jump to next line after print the output.
  
  
  
  
  // When hand is touched the sensor, the speaker will produce a tone.
  // I set a threshold for it, so that the sensor won't be too sensitive.
  if (total1 > 500) tone(speaker,131);   // frequency
  if (total2 > 500) tone(speaker,147);   // you can see https://www.arduino.cc/en/Tutorial/toneMelody if you want to change frequency
  if (total3 > 500) tone(speaker,165);
  if (total4 > 500) tone(speaker,175);
  if (total5 > 500) tone(speaker,196);
  if (total6 > 500) tone(speaker,220);
  if (total7 > 500) tone(speaker,247);
  if (total8 > 500) tone(speaker,262);
  
  // When hand didn't touch on it, no tone is produced.
  if (total1<=500  &  total2<=500  &  total3<=500 & total4<=500   e   total5 < = 500   e   total6 < = 500  e   total7 < = 500  e   total8 < = 500 )
     noTone ( orador ) ; 
  atraso ( 10 ) ;                              // atraso arbitrário para limitar os dados à porta serial 
 }



