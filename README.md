# CodCarrinho
#define va 2 //Pino de controle de velocidade do motor A
#define m1A 3 //Pino de alimentação do motor A 
#define m2A 4 //Pino de alimentação do motor A

void setup() {
  pinMode(va, OUTPUT); // Definição de porta do arduino como saída (OUTPUT)
  pinMode(m1A, OUTPUT); // Definição de porta do arduino como saída (OUTPUT)
  pinMode(m2A, OUTPUT); // Definição de porta do arduino como saída (OUTPUT)

  Serial.begin(9600); // Definição de frequencia da porta serial
}

void loop() {
  if(Serial.available()>0){ //Aqui o arduino vai analisar se está chegando alguma informação pelo serial (bluetooth)
    char valorRecebido = Serial.read(); //Caso receber o valor recebido pelo bluetooth será passado para dentro da variavel valorRecebido
    switch(valorRecebido){ //Aqui inicia o Switch case, ele avalia o que chegou no serial e compara com os cases abaixo
      case 'F':
        digitalWrite(m1A, HIGH); //Liga um dos pinos do motor para configurar o positivo
        digitalWrite(m2A, LOW); //Desliga um dos pinos do motor para configurar o negativo (GND)
        digitalWrite(va, 255); //Configura o máximo de velocidade para o funcionamento dos motores
      break; //Finaliza o case
    }
  }
}
