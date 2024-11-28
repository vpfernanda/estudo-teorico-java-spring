# Componentes e injeção de dependência
## Injeção de dependência
Quando um componente (por exemplo: uma classe) precisa de outro, é importante que haja um desacoplamento, embora um dependa de outro. Em termos práticos, deve-se evitar instanciar um objeto com a palavra chave **new** dentro de uma classe. Por exemplo:

_EVITA-SE:_  

```java
public class ClasseA {  
  private ClasseB objetoB = new ClasseB();  
  private ClasseC objetoC = new ClasseC();  
}
```
  
A abordagem acima torna o código muito acoplado, ou seja, alterações nos objetos instanciados tornaria necessario uma modificação da classe A. Imagine que a ClasseB não mais utilizasse um construtor padrão (sem argumentos). Em cada local que esta classe foi instanciada, seria necessário fazer uma alteração. 
Outra abordagem:

```java
public class ClasseA {  
  private ClasseB objetoB;
  private ClasseC objetoC;

  public ClasseA(ClasseB objetoB, ClasseC objetoC){
    this.objetoB = objetoB;
    this.objetoC = objetoC;
  }
```

Agora, temos um construtor que recebe esses objetos já instanciados. Isso torna o código menos acoplado e mais flexível. A essa abordagem dá-se o nome de injeção de dependência. Tais práticas são comuns na utilização de frameworks como _Spring_.


