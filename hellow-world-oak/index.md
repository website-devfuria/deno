---
title:       "OAK o 'express' do Deno"
description: Este é um exemplo de hellow world
capitulo:    oak
ordem:        1
---

Eis aqui um "hellow wolrd" com o framwork [oak](https://oakserver.github.io/oak/)

Crie um arquivo chamado `server.ts`.


    import { Application } from "https://deno.land/x/oak/mod.ts";

    const app = new Application();

    app.use((ctx) => {
      ctx.response.body = "Hello world!";
    });

    await app.listen("127.0.0.1:8080");


Execute `deno run --allow-net server.ts`.

Acesse em seu navegador http://localhost:8080/


### Uma segunda vesão

Abaix, temos uma versão ligeiramente diferente:

    import { Application } from "https://deno.land/x/oak/mod.ts";

    const app = new Application();
    const port: number = 8080;

    app.use((ctx) => {
      ctx.response.body = "Hello world!";
    });

    console.log("running on port ", port);

    await app.listen({ port });


### Este exemplo no GitHub

- [flaviomicheletti/deno-oak-getting-started](https://github.com/flaviomicheletti/deno-oak-getting-started)



### Error 'sorted' does not exist in type 'InspectOptions'

Se apareceu o erro abaixo para você, tente atualizar o Deno.

    error: TS2345 [ERROR]: Argument of type '{ depth: number; sorted: boolean; trailingComma: boolean; compact: boolean; iterableLimit: number; }' is not assignable to parameter of type 'InspectOptions'.
      Object literal may only specify known properties, and 'sorted' does not exist in type 'InspectOptions'.
            sorted: true,

            ~~~~~~~~~~~~

__Para atualizar__ eu executei o mesmo comando da instalação (para Linux):


    $ curl -fsSL https://deno.land/x/install/install.sh | sh

Obtive...

    ######################################################################## 100,0%##O#- #                                                        ######################################################################## 100,0%
    Archive:  /home/your-user/.deno/bin/deno.zip
      inflating: deno
    Deno was installed successfully to /home/you-user/.deno/bin/deno

Minha versão anterior era...

    deno --version
    deno 1.0.2
    v8 8.4.300
    typescript 3.9.2

Depois ficou...

    deno --version
    deno 1.2.1
    v8 8.5.216
    typescript 3.9.2

Voltei para o AOK e deu certo.

Veja mais info sobre este erro [aqui](https://github.com/denoland/deno/issues/6780)


