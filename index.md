---
layout:      secao
title:       Deno
description: Uma nova runtime para JavaScript
---

O Deno é um novo runtime segura para JavaScript e TypeScript.

O lançamento da sua versão 1.0 está chamando bastante atenção das comunidades de tecnologia no mundo.

Mas, afinal de contas, o que é o Deno ?

Ele substitui o Node.js ou alguma outra tecnologia ?

Será que ele substituirá o Nodejs ?

Quais são suas diferenças e propostas ?

Ryan Dahl, criador do Node, deu uma palestra em junho de 2018 na JSConf intitulada
[10 Coisas que eu lamento pelo Node.js](https://www.youtube.com/watch?v=M3BM9TB-8yA)
(10 Things I Regret About Node.js no original).

### Instalando o Deno no Linux

    curl -fsSL https://deno.land/x/install/install.sh | sh

Teste executando `deno`, deve abrir o REPL.

Ainda no terminal, execute o comando abaixo.

    deno run https://deno.land/std/examples/welcome.ts
    Welcome to Deno 🦕

Por curiosidade, acesse https://deno.land/std/examples/welcome.ts

    console.log("Welcome to Deno 🦕");


### Instalando no Windows

Abri o powershel e executei..

    iwr https://deno.land/x/install/install.ps1 -useb | iex

Obtive...

    Deno was installed successfully to C:\Users\flavio\.deno\bin\deno.exe
    Run 'deno --help' to get started

Da mesma forma que no Linux, testei da seguinte forma:

    deno run https://deno.land/std/examples/welcome.ts
    Welcome to Deno 🦕

Só o símbolo do dinossauro que falhou.


### Hello world com Deno

Eu peguei o trecho abaixo, coloquei em um arquivo e excutei.

    import { serve } from "https://deno.land/std@0.53.0/http/server.ts";

    const s = serve({ port: 8000 });

    console.log("http://localhost:8000/");

    for await (const req of s) {
    req.respond({ body: "Hello World\n" });
    }


O arquivo chama-se `01-basic.js` (você pode encontrá-lo [aqui](exemplos/01-basic.js))

Talvez você queira fazer o download deste repo [deno-hello-world](https://github.com/flaviomicheletti/deno-hello-world).

Eu executei dessa forma `deno run 01-basic.js`, ele começa a fazer dowload dos pacotes...

    Download https://deno.land/std@0.53.0/http/server.ts
    Download https://deno.land/std@0.53.0/encoding/utf8.ts
    Download https://deno.land/std@0.53.0/io/bufio.ts
    Download https://deno.land/std@0.53.0/testing/asserts.ts
    Download https://deno.land/std@0.53.0/async/mod.ts
    ...
    ...
    error: Uncaught PermissionDenied: network access to "0.0.0.0:8000", run again with the --allow-net flag

No final ele aprensentou um erro. Deno é seguro, certo ?

    deno run --allow-net 01-basic.js

...e voialá, basta acessar http://localhost:8000/


Observação, os comandos abaixo não fucionaram. Precisa ser como mostrado acima.

    deno --allow-net run 01-basic.js
    deno run 01-basic.js --allow-net flag


### Um exemplo de leitura de disco

Neste exemplo eu exploro a leitura em disco.

Precisaremos, ao executar o arquivo, utilizar o parâmetro `--allow-read`.

O código de exemplo é bem simples, possui apenas uma linha.

Repare que a extensão do arquivo é `ts` (typescript).

    console.log( Deno.cwd() )

O arquivo chama-se `02-basic.ts` (você pode encontrá-lo [aqui](exemplos/02-basic.ts))

    deno run --allow-read ./exemplos/02-basic.ts

A saída foi...

    Compile file:///home/flavio/devfuria.com.br/deno/exemplos/02-basic.ts
    /home/flavio/devfuria.com.br/deno


### Exemplo de teste uniario

Escrevendo testes unitários com Deno.

Abaixo vemos um exemplo:

    import { assert, equal } from "https://deno.land/std/testing/asserts.ts";

    Deno.test('the whole truth', () => {
        assert(1 === 1)
    })

    Deno.test('and nothing but the truth', () => {
        equal(1, 1)
    })

O arquivo chama-se `03-test.ts` (você pode encontrá-lo [aqui](exemplos/03-test.ts))

Para executar o teste use `deno test` conforme abaixo.

    deno test ./exemplos/03-test.ts

A saia dos testes é...

    running 2 tests
    test the whole truth ... ok (7ms)
    test and nothing but the truth ... ok (2ms)

    test result: ok. 2 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out (9ms)

Veja também [Harry Wollf - Writing tests with Deno](https://youtu.be/z06ggoeNnrk)


### Deno no Youtube

Ordem cronológica...

Cod3r:

- [DENO 1.0 chegou!! Testando o novo Runtime JavaScript e TypeScript!](https://youtu.be/cvF9fdWYy-4)

Progamador BR:

- [Deno - Conheça a Tecnologia que pode acabar com o Node](https://youtu.be/wQ93SqugjTw)
- [Deno - Instalando e criando meu primeiro WebServer](https://youtu.be/ckwk4VdxV34)

BrasilJS:

- [Deno: O que é e o que isso significa para o mundo Node.js](https://youtu.be/8lvOkqj4_W0)

ez.devs:

- [Criando uma API com Deno](https://youtu.be/aOtN5qdm7jY)

Código Fonte TV:

- [Deno (A alternativa ao Node.js !?)](https://youtu.be/fVoH6rFU6zw)
- [Construímos uma API Rest com Deno usando TypeScript que vai pra Produção](https://youtu.be/ThDTt_wd2Y4)


## Site Oficial

https://deno.land/

