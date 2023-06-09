# CRUD com NodeJS

Crie o arquivo `index.js`

    const express = require("express");
    const server = express();
    server.use(express.json());

    const cursos = [
      "FullStack Master",
      "Desenvolvimento de Games",
      "Viver de Youtube",
    ];

    // CRUD --> Create, Read, Update e Delete
    // Retorna um curso
    server.get("/cursos/:index", (req, res) => {
      const { index } = req.params;
      return res.json(cursos[index]);
    });

    // Retorna todos os cursos
    server.get("/cursos", (req, res) => {
      return res.json(cursos);
    });

    // Criar um novo curso
    server.post("/cursos", (req, res) => {
      const { name } = req.body;
      cursos.push(name);
      return res.json(cursos);
    });

    // Atualizar um curso
    server.put("/cursos/:index", (req, res) => {
      const { index } = req.params;
      const { name } = req.body;
      cursos[index] = name;
      return res.json(cursos);
    });

    // Deletar um curso
    server.delete("/cursos/:index", (req, res) => {
      const { index } = req.params;
      cursos.slice(index, 1);
      return res.json({ message: "O curso foi deletado" });
    });

    server.listen(3000);


`npm init -y` - Inicia npm no projeto criando arquivo package.json

`npm install express -save` - Instala o framework Express e suas dependências

`node index.js` - Iniciar servidor NodeJS
