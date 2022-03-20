# INTRODUÇÃO

## RELACIONAMENTO ENTRE O CATÁLOGO DE MENSAGENS DO SPI E O CATÁLOGO DE MENSAGENS DA ISO2002

As mensagens que cursam no Sistema de Pagamentos Instantâneos (SPI) utilizam o padrão 
ISO20022, conforme descrito no WebSite da ISO20022 Registration Authority, acessível em 
https://www.iso20022.org.

Essas mensagens são um subconjunto das mensagens previstas no padrão ISO, sendo que 
a forma de utilização de cada uma delas no SPI é definida no presente documento e em suas 
documentações anexas.

Em função do padrão ISO20022 ser definido de forma abrangente, com a possibilidade de 
contemplar diferentes cenários de uso, torna-se necessário indicar como cada mensagem será 
utilizada no caso brasileiro. Tal indicação mantém, no entanto, a compatibilidade com a norma 
original, indicando apenas, onde couber, restrições de uso adicionais.

Por exemplo, em uma dada mensagem, alguns atributos que são definidos no catálogo da 
ISO20022 como opcionais podem, no contexto de uso do SPI, ter preenchimento obrigatório. No 
entanto, é importante ressaltar que o contrário não ocorrerá. Atributos obrigatórios no catálogo da 
ISO20022 serão sempre tratados com obrigatórios no Catálogo do SPI.

Dessa forma, o presente documento trata do Catálogo de Mensagens do Sistema de 
Pagamentos Instantâneos, que estende definições oriundas do Catálogo de Mensagens da 
ISO20022.

## Formato de representação das mensagens

A forma de representação das mensagens ISO20022 adotada no SPI é o padrão Extensible 
Markup Language (XML), tal como apresentado no catálogo da norma (ver 
https://www.iso20022.org/iso-20022-message-definitions). O padrão de codificação utilizado é o 
UTF-8.

A validação sintática das mensagens será feita por meio de arquivos de definição do esquema 
XML (XML Schema Definition – XSD). Dessa forma, para cada mensagem definida no catálogo do 
SPI, existirá um XSD correspondente, que permitirá a sua validação, já considerando as 
especificidades do sistema.

## Detalhamento das mensagens do SPI

O detalhamento da forma de preenchimento das mensagens ISO20022 para uso no SPI 
encontra-se divulgado em arquivo compactado (zip), disponível em 
https://www.bcb.gov.br/estabilidadefinanceira/comunicacaodados.

O arquivo compactado segue a estrutura apresentada abaixo:


```
spi.1.2.zip
│ Notas de versão.pdf
├── exemplos
│ ├── admi.002
│ ├── pacs.002
│ ├── pacs.008
│ └── (...)
├── xsd
└── xslx
```


Na estrutura acima, as informações estão organizadas em uma estrutura de pastas e 
subpastas, detalhada a seguir. O nome do arquivo zip indica a versão do Catálogo do SPI contida 
na estrutura.

/ (pasta raiz)

O diretório raiz contém o arquivo Notas de versão.pdf, onde são informadas as alterações 
introduzidas em cada uma das versões do Catálogo.

/xsd

A pasta xsd contém os XML Schema Definitions de cada uma das mensagens, seguindo o 
padrão de nomenclatura exemplificado a seguir:

- admi.002.spi.1.2.xsd
- pibr.001.spi.1.0.xsd

É importante observar que a versão indicada no nome do arquivo equivale a versão da 
mensagem específica, que não se confunde com a versão do Catálogo. Ou seja, uma dada 
versão do Catálogo pode conter diferentes versões de mensagens.
Esta pasta conterá também o xsd referente padrão de assinatura utilizado (XMLDSig):

xmldsig.0.1.xsd

/exemplos 

Essa pasta contém exemplos das mensagens usando o padrão XML, organizadas em 
subpastas para cada uma das mensagens. Os nomes dos XMLs indicam o contexto do 
exemplo específico:

- pacs.008.spi.1.2_CONTA_1_msg.xml
- pacs.008.spi.1.2_END_1_msg.xml

/xlsx

A pasta xlsx contém as orientações de preenchimento de cada uma das mensagens, bem 
como os domínios dos campos controlados.

Ressalte-se que o Business Application Header tem sua forma de preenchimento indicada no 
arquivo XLSX, mas não aparece entre os XSDs de forma individual. Isso ocorre porque o BAH já 
está envelopado no XSD de cada uma das mensagens individuais (ver tag <AppHdr>)

## Informações de data e hora

Todas as mensagens do SPI são expressas no padrão UTC (Coordinated Universal Time), o 
que indica, além do uso da letra ‘Z’ do indicador do padrão, que existirá uma defasagem na data e 
hora expressa na mensagem com relação a data e hora de Brasília. Considerando o horário padrão, 
essa diferença será de três horas. Ou seja, o horário de Brasília equivale a horário UTC menos 
três horas.

Nesse sentido, os timestamps normalmente são expressos no padrão abaixo:

>YYYY-MM-DD'T'hh:mm:ss.sss'Z'




