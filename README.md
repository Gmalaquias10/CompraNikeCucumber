package br.ce.gmalaquias.steps;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

import cucumber.api.java.pt.Dado;
import cucumber.api.java.pt.Entao;
import cucumber.api.java.pt.Então;

public class CompraNikeSteps {
	WebDriver driver;
	
	
	
	@Dado("^que estou acessando o site da nike$")
	public void queEstouAcessandoOSiteDaNike() throws Throwable{
		System.setProperty("webdriver.chrome.driver", "C:\\Users\\anton\\Documents\\chromedriver\\chromedriver\\chromedriver.exe");
	    driver = new ChromeDriver();
		driver.get("https://www.nike.com.br/"); 
		
	}

	@Dado("^vou na aba pesquisar e informo o nome (.*)$")
	public void vouNaAbaPesquisarEInformoONome(String camisa) throws Throwable{
		driver.findElement(By.xpath("//button[@class='ButtonFill__StyledButton-sc-d418d4ee-0 djoXVp']")).click();
		driver.findElement(By.name("search")).sendKeys("Regata Dallas");
		Thread.sleep(5000);
		driver.findElement(By.xpath("//button[@class='ButtonIcon__StyledButton-sc-wd4o68-0 hScimd']")).click();		
		Thread.sleep(5000);
	}

	@Então("^visualizo a regata e seleciono o modelo$")
	public void visualizoARegataESelecionoOModelo()throws Throwable {
		driver.findElement(By.xpath("//div[@class='ProductCard-styled__ProductName-sc-8f840517-9 iKtbYK']")).click();
		Thread.sleep(5000);
	   
	}

	@Então("^seleciono o (.*)$")
	public void selecionoOTamanho(String tamanho)throws Throwable {
		driver.findElement(By.xpath("//input[@data-testid='product-size-GGGG']")).click();
		Thread.sleep(5000);
	
	}

	@Entao("^adiciono ao Carrinho$")
	public void adicionoAoCarrinho()throws Throwable {
		driver.findElement(By.xpath("//button[@class='ButtonFill__StyledButton-sc-d418d4ee-0 hYCukR']")).click();
	}
}