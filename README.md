# Danger-Track

Integrantes
---
Pedro Henrique Silva | RM97432
Pedro Gava | RM551043
Eric Rodrigues | RM550249
Anny Dias | RM98295
Henrique Lima | RM551528

---

Projeto Danger Track: Inteligência Artificial e Hardware a Serviço da Segurança Urbana
1. Introdução e Visão Geral
A segurança pública é um dos maiores desafios das metrópoles brasileiras, especialmente em São Paulo. O Danger Track surge como uma plataforma de monitoramento inteligente projetada para transformar a vigilância urbana. O projeto propõe a integração do parque tecnológico existente (câmeras municipais) a uma rede de drones autônomos, utilizando visão computacional e análise de dados em tempo real para identificar e reportar incidentes criminais de forma instantânea e preventiva.

2. O Problema
Atualmente, a maioria dos sistemas de vigilância opera de forma reativa: as imagens servem apenas para registros pós-crime, sem capacidade de intervenção imediata. Os principais problemas identificados são:

Lacunas de Atenção: O monitoramento depende excessivamente da visão humana, sujeita a falhas.

Tempo de Resposta Lento: Crimes como furtos, brigas e agressões ocorrem sem que as autoridades sejam notificadas a tempo.

Insegurança Crescente: A ausência de análise inteligente em tempo real contribui para a vulnerabilidade de espaços públicos e comerciais.

3. Arquitetura da Solução: Do Protótipo à Escala Real
O projeto Danger Track foi estruturado em duas etapas complementares que unem hardware de baixo custo à inteligência artificial avançada.

3.1. Prova de Conceito: Protótipo em Tinkercad
Para validar a lógica de detecção automática de alterações, foi desenvolvido um protótipo utilizando a plataforma Tinkercad. Este modelo simula o comportamento de uma câmera inteligente monitorando um objeto ou área específica.

Componentes: Arduino Uno, Sensor LDR (Light Dependent Resistor), LEDs indicadores (Verde/Vermelho) e Resistores.

Funcionamento: O sensor LDR monitora a intensidade luminosa/presença. Quando o estado padrão é alterado (simulando a retirada de um objeto ou invasão de perímetro), o sistema alterna do LED verde (Normal) para o LED vermelho (Alerta), validando o fluxo de detecção e resposta imediata.

3.2. Implementação em Escala: O Ecossistema Danger Track
A lógica validada no protótipo expande-se para um ecossistema complexo na cidade:

Rede Neural de Vigilância: Software de IA implementado nas câmeras da cidade, treinado para reconhecer padrões de movimento (saque de armas, agressões ou movimentações suspeitas).

Unidades Aéreas de Resposta (Drones): Drones equipados com câmeras HD e sensores infravermelhos que patrulham áreas críticas ou são deslocados automaticamente para locais onde o sistema fixo detectou um incidente.

4. Fluxo de Operação
Detecção Automática: O algoritmo ou o sensor identifica uma situação de risco em tempo real.

Triagem e Verificação: O sistema cruza dados e, se necessário, aciona um drone próximo para obter ângulos detalhados.

Acionamento Prioritário: Confirmado o incidente, um alerta georreferenciado com imagens e rotas de fuga é enviado instantaneamente ao Centro de Operações da Polícia.

5. Diferenciais e Impacto Social
Diferente dos sistemas tradicionais, o Danger Track realiza uma análise ativa e preventiva. Seus principais benefícios incluem:

Resposta Imediata: Redução drástica no tempo entre a ocorrência e a chegada da polícia.

Prevenção: Aumento da percepção de vigilância, inibindo a ação de criminosos.

Eficiência Tecnológica: Utilização de Edge Computing para processar dados localmente e reduzir custos de infraestrutura.

6. Conclusão
A segurança pública exige inovação que vá além da simples gravação de imagens. O projeto Danger Track demonstra que é possível unir tecnologia acessível (como o protótipo em Arduino) a soluções de alta complexidade (IA e Drones) para antecipar problemas e proteger o cidadão.
A proposta não busca apenas monitorar; busca antecipar, proteger e transformar a segurança urbana por meio da tecnologia.


<img width="403" height="603" alt="image" src="https://github.com/user-attachments/assets/07afcd31-d399-4489-814b-e0f278fb00a3" />

<img width="2816" height="1536" alt="Gemini_Generated_Image_bhhkhtbhhkhtbhhk" src="https://github.com/user-attachments/assets/d5a9a872-04cb-4fec-bf0d-b869bfc8d7ac" />



https://github.com/user-attachments/assets/baeba296-7299-469a-9625-64c4ce499f3a


<img width="1038" height="654" alt="imagem" src="https://github.com/user-attachments/assets/be72f32b-93dc-48cc-9fb3-53a1bf0f9e98" />
<img width="1031" height="669" alt="imagem (1)" src="https://github.com/user-attachments/assets/a107bf26-d360-45be-9964-6733b84fe4ed" />



---
Código tinkercad:
const int ldrPin = A0;
const int ledVerde = 2;
const int ledVermelho = 3;
 
int valorLDR;
int limite = 500; // ajuste se necessário
 
void setup() {
  pinMode(ledVerde, OUTPUT);
  pinMode(ledVermelho, OUTPUT);
  Serial.begin(9600);
}
 
void loop() {
  valorLDR = analogRead(ldrPin);
  Serial.println(valorLDR);
 
  if (valorLDR < limite) {
    // Objeto tampando a luz
    digitalWrite(ledVerde, HIGH);
    digitalWrite(ledVermelho, LOW);
  } else {
    // Luz incidindo → objeto removido
    digitalWrite(ledVerde, LOW);
    digitalWrite(ledVermelho, HIGH);
  }
 
  delay(300);
}
