---
title: "Escrevendo classes coesas aplicando SRP"
description: "Com certeza, a coesão é uma das palavras amplamente reconhecidas pelos programadores que trabalham com linguagens orientadas a objeto. Seu significado é bastante claro: uma classe é considerada coesa quando possui uma única responsabilidade, evitando abranger mais de um contexto no sistema."
pubDate: "Jul 20 2023"
badge: "#OOP"
tags: ["SOLID", "SRP"]
slug: "escrevendo-classe-coesa-aplicando-srp"
---

<p style="text-align: justify">
    Com certeza, a <b>coesão</b> é uma das palavras amplamente reconhecidas pelos programadores que trabalham com linguagens orientadas a objeto. Seu significado é bastante claro: <u>uma classe é considerada coesa quando possui uma única responsabilidade</u>, evitando abranger mais de um contexto no sistema. Por exemplo, se uma classe é encarregada de representar uma nota fiscal, ela se dedica exclusivamente a essa tarefa, enquanto as responsabilidades relacionadas a uma fatura estarão atribuídas a outra classe.
</p>

<p style="text-align: justify">
    É indiscutivel a necessidade de se criar entidades coesas em um sistema orientado a objetos.
    Os motivos são: 
    <ul>
        <li>são mais simples de serem mantidas;</li>
        <li>possuem menos código;</li>
        <li>maior reusabilidade;</li>
    </ul>
</p>

<p>Considere o exemplo abaixo:</p>

```javascript
class Student {

     registerStudent() {
         // some logic
     }

     calculateStudentResults() {
         // some logic
     }

     sendEmail() {
         // some logic
     }
}
```
<p style="text-align: justify">
    Por que a classe acima viola o princípio da responsabilidade única?
    Esta classe <b>Student</b> tem três responsabilidades:
      <ul>
        <li>registrar alunos;</li>
        <li>calcular seus resultados;</li>
        <li>enviar e-mails aos alunos;</li>
    </ul>
</p>

<p style="text-align: justify">
    Embora o código acima funciona perfeitamente, porém ele apresentará alguns desafios significativos. 
    A reutilização desse código em outras classes ou objetos não é possível, pois a classe possui uma lógica muito interconectada, dificultando a correção de erros. À medida que a base de código cresce, a complexidade da lógica também aumenta, tornando ainda mais complicado compreender o que está ocorrendo.
</p>

<p style="text-align: justify">
    Considere um novo membro da equipe de desenvolvimento se juntando a um projeto com esse tipo de lógica, onde a base de código contém cerca de duas mil linhas, todas confinadas em uma única classe 🤬.
</p>

Agora vamos consertar isso!

```javascript
class StudentRegister {
    registerStudent() {
        // some logic
    }
}

class StudentResult {
    calculateStudentResult() {
        // some logic
    }
}

class StudentEmails {
    sendEmail() {
        // some logic
    }
}
```
<p style="text-align: justify">
    Agora separamos cada funcionalidade em nosso programa. Podemos chamar as classes em qualquer lugar que quisermos para usá-las em nosso código.
</p>
<p style="text-align: justify">
    Os exemplos que usamos mostram apenas que cada classe tem um método – isso é principalmente para simplificar. Você pode ter quantos métodos quiser, mas eles devem estar vinculados à responsabilidade da classe.
</p>
<p style="text-align: justify">
    Agora que separamos a lógica, nosso código fica mais fácil de entender, pois cada funcionalidade principal tem sua própria classe. Podemos testar os erros com mais eficiência.
    O código agora é reutilizável. Antes, só podíamos usar essas funcionalidades dentro de uma classe, mas agora elas podem ser usadas em qualquer classe.
    O código também é de fácil manutenção e escalabilidade porque, em vez de ler linhas de código interconectadas, separamos preocupações para que possamos nos concentrar nos recursos nos quais queremos trabalhar.
</p>