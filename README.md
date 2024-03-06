# Desafio - Machine Learning Azure - Bootcamp Microsoft Azure AI Fundamentals da Dio.me

Passo a passo do experimento de Aprendizaem Automatizada, utilizando a **Azure Machine Learning**

Link da documentação: <https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html>



1 - Criamos conta no <https://azure.microsoft.com/pt-br/free>;

2 - Inicicamos com o cadastro no site usando o caminho  '**Experimentar grátis**' - nesse caso precisamos utilizar um cartão de crédito válido, mas lembrar de excluir o cartão, já que estamos apenas testanto por um périodo;

3 - Acessamos a plataforma do Azure <portal.azure.com>;

4 - Buscamos por '**Azure Machine Learning**' no campo de busca;

5 - Clicamos em **Criar** > **Novo Workspace**;

6 - Criamos um novo 'Grupo de recursos', dando um nome, em 'Detalhes do workspace' adicionamos as informações de 'nome' e 'região'. As outras informações como 'conta, Cofre... já serão preenchiadas, não as alteramos;

7  - Clicamos em '**Examinar e Criar**', após irá para uma tela com o alerta 'validação aprovada', e então, clicamos em '**criar**';

8 - Lava alguns minutos com o alerta em tela 'Implantação em andamente', até que finalize a implantação com a mensagem 'A implantação foi concluída';

9 - Nesta dela chamada 'deployment' clicamos em '**Ir para recurso**';

10  - Na tela de 'Recursos' clicamos em '**Iniciar estúdio**';

11 - Na tela de Estúdio conseguimos acessar 'Todos os espaços de trabalho' e acessamos todos os "Warkspaces" existentes;

12 - Clicamos no Espaço de trabalho recém criado (ou no qual escolhermos) e clicamos em '**ML Automatizado**' > '**Novo trabalho de ML automatizado**' para acessarmos no Ambiente;

13 - Na tela preenchemos os dados do trabalho, com as informações fornecidas pela documentação da Microsoft, por tópicos clicando em 'Avançar', segue abaixo:
 
    Configurações básicas :

    Nome do trabalho : mslearn-bike-automl
    Novo nome do experimento : mslearn-bike-rental
    Descrição : Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
    Marcadores : nenhum

	
    Tipo de tarefa e dados :

    Selecione o tipo de tarefa : Regressão
		
14 - Clicamos em '**Criar**' e preenchemos com os dados abaixo: 

		Tipo de dados :
	
    Nome : aluguel de bicicletas (sem espaço, se não, dá erro)
    Descrição : dados históricos de aluguel de bicicletas
    Tipo : Tabular

15 - Após clicarmos em 'Avançar' selecionamos a opão '**Dos arquivos da web**' em Fonte de dados;

16 - Avançamos e chegamos em 'Url da Web', preenchemos assim:

	  URL da Web :https://aka.ms/bike-rentals
    Ignorar validação de dados : não selecionar

17 -  Avançamos e chegamos em 'Configurações', preenchemos os campos:

			Formato de arquivo : Delimitado
      Delimitador : Vírgula
      Codificação : UTF-8
      Cabeçalhos de coluna : apenas o primeiro arquivo possui cabeçalhos
      Pular linhas : Nenhum
      O conjunto de dados contém dados multilinhas : não selecione

18 - Ao avançarmos, chegamos na tela 'Esquema', não é necessário executar nenhuma atividade nesta página, apenas clicamos em '**avançar**';

19 - Chegamos no tópico 'Examinar', verificamos um resumo,  se as informações estão de acordo com a documentação e clicamos em '**Criar**';

20 - Após a ativação de dados, no fim da página em 'Selecionar dados', selecionamos o nosso dado recém criado '**algueldebicicletas** e clicamos em '**Avançar**';

21 - Preenchemos e verificamos as 'Configurações de tarefas' como os dados abaixo:

     Tipo de tarefa : Regressão
     Conjunto de dados : aluguel de bicicletas
     Coluna de destino : Rentals (inteiro)
		 
     Configurações adicionais :
     Métrica primária : raiz do erro quadrático médio normalizado / normalized root mean square error
     Explique o melhor modelo : Não selecionado
     Usar todos os modelos suportados : Desmarcado . Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.
     Modelos permitidos : Selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o máximo possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.

 22 - **Salva** e vamos para o preencimento das informações de 'Limites' (expadimos a seção) e 'Validar e testar' com os dados abaixo:

    Máximo de testes : 3
    Máximo de testes simultâneos : 3
    Máximo de nós : 3
    Limite de pontuação da métrica : 0,085 ( para que, se um modelo atingir uma pontuação da métrica de erro quadrático médio normalizado de 0,085 ou menos, o trabalho termina. )
    Tempo limite : 15
    Tempo limite de iteração : 15
    Habilitar rescisão antecipada : selecionado

    Tipo de validação : divisão de validação de treinamento
    Porcentagem de dados de validação : 10
    Conjunto de dados de teste : Nenhum
    

23 - Chegamos no tópico 'Computação', aqui não fazemos nehuma alteração, só validamos com as informações da documentação:
 
     Selecione o tipo de computação : sem servidor
     Tipo de máquina virtual : CPU
     Camada de máquina virtual : Dedicada
     Tamanho da máquina virtual : Standard_DS3_V2*
     Número de instâncias : 1

24 - Chegamos em 'Examinar', clicamos em '**Enviar trabalho de treinamento**', ele ficará em Execução por uns 10 a 20 minutos;

25 - Após a exucação, quando o trabalho automatizado de aprendizado de máquina for concluído, podemos revisar o melhor modelo treinado na guia 'Visão Geral';

27 - Selecionamos o link no quadro 'Melhor resumo do modelo' abaixo de 'Nome de Algoritmo' para visualizarmos melhor os detalhes;

28 - Na guia 'Métricas', selecionamos os gráficos **residuais** e **predito_true** se eles ainda não estivrem selecionados;

29 - Na guia 'Modelo', selecionamos '**Implantar**' e usamos a opção **servidor Web** para implantar o modelo com as configurações abaixo e clicamos em '**implantar**':

		 Nome : prever-alugueis
     Descrição : Prever aluguel de bicicletas
     Tipo de computação : Instância de Contêiner do Azure
     Habilitar autenticação : selecionado
  
     

 30 - Aguardamos a notificação e/ou veificamos em tela do status da implantação como 'Concluído', isso deve demorar uns minutos;

 31 - Agora vamos testar o serviço implantado no Estúdio Azure Machine Learning, do lado esquerdo, selecionamos '**Pontos de Extremidade**' > (nome)'**prever-alugueis**' > '**testar**'

 32 - Substituímos o código em tela pelo baseando-se pela documentação e clicamos em '**testar**'

   		 {
     "Inputs": { 
     "data": [
       {
         "day": 5,
         "mnth": 3,   
         "year": 2024,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]    
     },   
       "GlobalParameters": 1.0
    }
 

  33 - Em tela saíra o resultado do teste, nele usamos um conjunto de dados históricos de aluguel debicicletas para treinar um modelo. O modelo prevê o número de alugueres de bicicletas esperados num determinado dia, com base em características sazonais e meteorológicas.
	
	 
   	{
    "Results": [
    396.88726582845254
      ]
    }

 
  
			 

