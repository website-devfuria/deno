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


### Instalando o Deno no Linux

    curl -fsSL https://deno.land/x/install/install.sh | sh

Teste executando `deno`, deve abir o REPL.

Ainda no terminal, execute o comando abaixo.

    deno run https://deno.land/std/examples/welcome.ts
    Welcome to Deno 🦕

Por curiosidade, acesse https://deno.land/std/examples/welcome.ts

    console.log("Welcome to Deno 🦕");

### Hello world com Deno

Eu peguei o trecho abaixo, coloquei em um arquivo e excutei.

    import { serve } from "https://deno.land/std@0.53.0/http/server.ts";
    const s = serve({ port: 8000 });
    console.log("http://localhost:8000/");
    for await (const req of s) {
        req.respond({ body: "Hello World\n" });
    }

O arquivo chama-se `01-basic.js` (você pode encontrá-lo [aqui](exemplos/01-basico.js))

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


Observação, os comando abaixo não fucionaram. Precisa ser como mostrado acima.

    deno --allow-net run 01-basic.js
    deno run 01-basic.js --allow-net flag



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



## Site Oficial

https://deno.land/

