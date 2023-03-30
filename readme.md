# Projeto 1 - Aplicação web progressiva

## Nome da aplicação: Cursos finalizados

A aplicação em questão é uma plataforma que lista cursos finalizados. Nela, os usuários podem visualizar uma variedade de cursos de diferentes áreas do conhecimento que já foram concluídos.

## Páginas

Home e Lista de cursos

## Dados armazenados

Lista de Cursos e Data

### A aplicação é original e não uma cópia da aplicação de um colega ou de uma aplicação já existente?
Não
### A aplicação tem pelo menos duas interfaces (telas ou páginas) independentes?

Sim

### A aplicação armazena e usa de forma relevante dados complexos (mais de um atributo)?

Sim

### A aplicação possui um manifesto para instalação no dispositivo do usuário?

Sim

### A aplicação possui um service worker que permite o funcionamento off-line?

Sim

### O código da minha aplicação possui comentários explicando cada operação?

Sim

### A aplicação está funcionando corretamente?

Sim

### A aplicação está completa?

Sim


## HTML

A aplicação possui uma formatação de HTML básico utilizando tags padrões
como por exemplo :
    ```<ul>``` ```<li>``` ```<button>```
    
## CSS

Após o html foi inserido a estilização simples com o css
   
## Javascript

Após o visual, o service work é implementado através do código padrão abaixo:
```
 if ('serviceWorker' in navigator) {
      window.addEventListener('load', function() {
        navigator.serviceWorker.register('/sw.js').then(function(registration) {
          console.log('sucesso:', registration.scope);
        }, function(err) {
          console.log('Falha :', err);
        });
      });
    }

```

O código acima implementa segundo plano e execute tarefas mesmo quando o usuário não está interagindo com a página.

No trecho abaixo um ouvinte de eventos que é acionado quando um formulário é enviado pelo usuário. Ele impede que o formulário seja enviado e atualize a página, e em seguida, obtém o valor do item digitado pelo usuário e cria uma string de data formatada. O código cria um novo elemento HTML "li" com a data e o item digitado e o adiciona a uma lista existente. Finalmente, o código limpa o campo de texto onde o item foi digitado.

```
    form.addEventListener('submit', function(event) {
      event.preventDefault();
      const item = document.querySelector('#item').value;
      const date = new Date().toLocaleDateString('pt-BR');
      const listItem = document.createElement('li');
      listItem.innerHTML = `<span class="date">Data conclusão: ${date}</span> ${item} <button class="edit">Editar</button>`;
      list.appendChild(listItem);
      document.querySelector('#item').value = '';
    });

```

De maneira resumida o código abaixo adiciona um ouvinte de eventos que permite editar itens de uma lista clicando em um botão "Editar" e salvando as alterações com um botão "Salvar".
```
  list.addEventListener('click', function(event) {
      if (event.target.classList.contains('edit')) {
        const listItem = event.target.parentNode;
        const itemText = listItem.textContent;
        const editInput = document.createElement('input');
        editInput.type = 'text';
        editInput.value = itemText;
        const saveButton = document.createElement('button');
        saveButton.textContent = 'Salvar';
        listItem.appendChild(editInput);
        listItem.appendChild(saveButton);
        event.target.style.display = 'none';
        saveButton.addEventListener('click', function() {
          listItem.textContent = editInput.value;
          event.target.style.display = 'block';
        });

```


