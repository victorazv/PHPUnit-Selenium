- Instalar o Wamp
- Instalar o Composer
- Instale o PHPUnit de forma global - composer global require "phpunit/phpunit=4.6.*" 
	Certifique que o phpunit está no PATH do seu sistema.
	Para ter certeza que o PHPUnit está ok, execute: phpunit --version
		Caso não esteja, adiciona nas variáveis de ambiente a pasta do PHPUnit
Instale as dependências do projeto, dê o comando composer install no cmd estando na pasta do composer.json
Faça download do webdriver do Chrome para seu SO. - 
	http://chromedriver.storage.googleapis.com/index.html?path=2.20/
Faça o download do servidor do Selenium 
	http://www.seleniumhq.org/download/
Inicie o servidor do PHP na pasta webapp
	php -S localhost:8000 -t webapp
Inicie o servidor do Selenium
	Para testar com Chrome: java -jar selenium-server-standalone-2.48.2.jar -Dwebdriver.chrome.driver=/Users/SeuUsuario/Caminho/Para/chromedriver
	Para testar com Chrome no Windows: java -jar selenium-server-standalone-2.48.2.jar -Dwebdriver.chrome.driver="C:\Users\victo\Downloads\UnitSelenium-master\chromedriver.exe" -- Caminho até o Driver
	Para testar com FireFox: java -jar selenium-server-standalone-2.48.2.jar

Se for testar com o Firefox, é necessário algumas modificações no arquivo de teste
	// testes/testeTitulo.php ou testes/testeFormulario.php
	// Linha 19 - Trocar
	$driver = RemoteWebDriver::create($hostDoSelenium, DesiredCapabilities::chrome());
	// Para
	$driver = RemoteWebDriver::create($hostDoSelenium, DesiredCapabilities::firefox());

	// Linha 23 - Trocar
	$this->setBrowser('chrome');     
	// Para
	$this->setBrowser('firefox');

Executando os testes

Teste do Título da Página
	phpunit testes/testeTitulo.php
Teste do Formulário
	phpunit testes/testeFormulario.php