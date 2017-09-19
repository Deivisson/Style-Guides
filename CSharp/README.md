# CSharp Style Guide
*Uma abordagem prática para escrita de codigos c#*

## Conteúdo

1. [Convenção Capitlaização](#)
1. [Convenção Nomeação](#)
1. [Nomes de Classes, Estruturas e Interfaces](#)
1. [Identações](#)


**Convenção Capitlaização**

Existem basicamente duas formas de capitalizações, PascalCasing e camelCasing

PascalCasing: Primeira letra de cada palavra em maiusculo
camelCasing: Primeira Letrar minusculo e o restante maiusculo. O camelCasing é basicamente utilizado para parametros e variáveis de scopo local.

Exemplos de uso:
//Namespaces
//ruim
namespace cadastros {...}

//bom 
namespace Cadastros {...}

//Types
//ruim 
public class contaBancaria {...}

//bom 
public class ContaBancaria { ... }

// Interface
//ruim
public interface Pessoa { ... }

//bom 
public insterface IPessoa { ... }

//Methods
//ruim 
public class ContaBancaria 
{
	public static void recuperarPorCodigo { ... }
	public static void recuperar_por_codigo { ... }
}

//bom 
public class ContaBancaria 
{
	public static void RecuperarPorCodigo { ... }
}

//Propriedades 
// ruim
public class ContaBancaria 
{
	public int codigoInterno {get;set;}
	public int codigo_interno {get;set;}
}

// bom
public class ContaBancaria 
{
	public int CodigoInterno {get;set;}
}

// Parametros 
// ruim
public class ContaBancaria
{
	public static RecuperarPorCodigo(int CodigoInterno) {...}
	public static RecuperarPorCodigo(int codigo_interno) {...}
}

// bom
public class ContaBancaria
{
	public static RecuperarPorCodigo(int codigoInterno) {...}
}


**Convenção Nomeação**

//Escolha termos de fácil leitura e boa coerência.
// ruim 
MensalExtrato

// bom
//ExtratoMensal

Prefira Legibilidade ao invés de abreviações
// ruim 
int LimDia = 2

// bom 
int LimiteSaqueDiario = 2

Não utilizar Hungarian Notation
Obs: Hungarian notation é a tecnica de adicionar prefixo aos nomes, isto caiu em desuso pelo fato da evolução das IDEs e por prejudicar a legibilidade do codigo.

// ruim 
string strTitular = "";
date dtAberturaConta  = null;

// bom
string Titular = "";
date DataAberturaConta = null;

Evite o uso de palavras reservadas da Linguagem
// ruim
string ReturnNome = "";


** Nomes de Classes, Estruturas e Interfaces **

- Nomes de Classes e Estruturas utilize substantivos ou frases nominais 
- Não utilizar o prefixo "C" para nomes de classes:
// ruim
public class CFornecedor {...}

- Nomes de Interfaces dê preferencia para o uso de adjetivos e ocasionalmente substantivos ou frases nominais 
- Utilize o prefixo "I" para nomes de interfaces

- Nomes de Enuns
	* Use nomes singulares
	* Não utilize sufixo Enum

- Nomes de Métodos
	* Utilize Verbos ou Frases verbais

	public class ContaBancaria 
	{
		public double ObterSaldo() {...}
		public string Salvar() { ... }
	}

- Nomes de Propriedades
	* Utilize substantivos, frases nominais ou adjetivos
	* Considere utilizar nomes de propriedades com o mesmo nome do tipo. Ex:
	public Enum TipoConta { ... }
	public class ContaBancaria 
	{
		public TipoConta TipoConta {get;set;}
	}

- Nomes de Eventos
	* Eventos arremete a ação, portanto utilize verbos ou frases verbais
		Ex: Clicked, DroppedDown

	* Não utilize prefixos para indicar pré ou pós eventos, tipo AntesClicado, AposClicado
	* Utilize dois parametros (sender, e), em event handlers
	