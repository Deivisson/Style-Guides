# CSharp Style Guide
*Uma abordagem prática para escrita de codigos c#*

## Conteúdo

1. [Convenção Capitalização](#convenção-capitalização)
1. [Convenção Nomeação](#convenção-nomeação)
1. [Nomes de Classes, Estruturas e Interfaces](#nomes-de-classes,-estruturas-e-interfaces)
1. [Comentários](#comentários)
1. [Referências](#referências)

## Convenção Capitalização

Existem basicamente duas formas de capitalizações, PascalCasing e camelCasing

PascalCasing: Primeira letra de cada palavra em maiusculo
camelCasing: Primeira Letrar minusculo e o restante maiusculo. O camelCasing é basicamente utilizado para parametros e variáveis de scopo local.

Exemplos de uso:
- Namespaces
```c#
//ruim
namespace cadastros {...}

//bom 
namespace Cadastros {...}
```
- Types
```c#
//ruim 
public class contaBancaria {...}

//bom 
public class ContaBancaria { ... }
```
- Interface
```c#
//ruim
public interface Pessoa { ... }

//bom 
public insterface IPessoa { ... }
```

- Méthods
```c#
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
```

- Propriedades 
```c#
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
```

- Parâmetros 
```c#
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
```

## Convenção Nomeação

- Escolha termos de fácil leitura e boa coerência.

```c#
// ruim 
MensalExtrato

// bom
//ExtratoMensal
```

- Prefira Legibilidade ao invés de abreviações
```c#
// ruim 
int LimSqDia = 2

// bom 
int LimiteSaqueDiario = 2
```

- Não utilizar Hungarian Notation
Obs: Hungarian notation é a técnica de adicionar prefixo aos nomes, isto caiu em desuso pelo fato da evolução das IDEs e por prejudicar a legibilidade do código.

```c#
// ruim 
string strTitular = "";
date dtAberturaConta  = null;

// bom
string Titular = "";
date DataAberturaConta = null;
```

- Evite o uso de palavras reservadas da Linguagem
```c#
// ruim
string ReturnNome = "";
```
## Nomes de Classes, Estruturas e Interfaces

- Nomes de Classes e Estruturas utilize substantivos ou frases nominais 
- Não utilizar o prefixo "C" para nomes de classes:

```c#
// ruim
public class CFornecedor {...}

```
- Nomes de Interfaces dê preferencia para o uso de adjetivos e ocasionalmente substantivos ou frases nominais 
- Utilize o prefixo "I" para nomes de interfaces
- Nomes de Enuns
	* Use nomes singulares
	* Não utilize sufixo Enum

- Nomes de Métodos
	* Utilize Verbos ou Frases verbais

```c#
public class ContaBancaria 
{
  public double ObterSaldo() {...}
  public string Salvar() { ... }
}
```

- Nomes de Propriedades
	* Utilize substantivos, frases nominais ou adjetivos
	* Considere utilizar nomes de propriedades com o mesmo nome do tipo. Ex:
```c#
public Enum TipoConta { ... }
public class ContaBancaria 
{
  public TipoConta TipoConta {get;set;}
}
```

- Nomes de Eventos
	* Eventos arremete a ação, portanto utilize verbos ou frases verbais
		Ex: Clicked, DroppedDown

	* Não utilize prefixos para indicar pré ou pós eventos, tipo AntesClicado, AposClicado
	* Utilize dois parametros (sender, e), em event handlers

## Comentários
- Comentário de uma linha
```c#
public string ValidarDescricaoProdutoImportado(string descricao)
{
  // Foi necessário remover a quebra de linha, para que não ocorra erro ao Exportar Carga de produtos para o PDV 	
  return descricao.replace('\n','')
}
```

- Comantário de Documentação

Utilizado para documentar métodos, classes e etc.. com uma breve descrição do seu objetivo.
```c#
/// <summary>
/// PUT api/produtos/:id
/// Atualiza informações de determinado produto 
/// </summary>
/// <param name="produto">Objeto com atributos a serem atualizados</param>
/// <returns>Objeto do tipo Produto atualizado</returns>
public HttpResponseMessage Put(int id, [FromBody]Produto values)
{
    Produto produto = Produto.LocalizarPorCodigo(id);
    HttpResponseMessage response = new HttpResponseMessage(HttpStatusCode.NotFound);
    if (produto != null)
    {
	bool atualizado = produto.AtualizarAtributos(values);
	response = new HttpResponseMessage(atualizado ? HttpStatusCode.OK : HttpStatusCode.NotModified);
    }
    return response;
}
```

## Referências
* https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions#commenting-conventions
* https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/index
