---
slug: como-usar-nodemailer-e-gmail
title: Como usar o Nodemailer com o Google
authors: [devluar]
tags: [nodejs]
---

Fala devs! Nesse post mostro em simples passos como podem conectar sua conta gmail com o nodemailer.

Requisitos:
- NodeJS instalado
- Editor de código com terminal integrado (Ex: [Visual Studio Code](https://code.visualstudio.com))
- Nodemailer pré-instalado

## Criação da Senha de App

Acesse o URL https://myaccount.google.com/apppasswords e crie uma senha de app.
Depois copie a senha gerada.

## Configuração no nodemailer

```javascript
const transporter = nodemailer.createTransport({
   service: "gmail",
  auth: {
    user: "seuemail@gmail.com",
    pass: "senha_do_app",
  },
});
```

e pronto, agora só fazer suas funções de envio de e-mail!

Código completo se quiser:

```javascript
const nodemailer = require("nodemailer");

const transporter = nodemailer.createTransport({
   service: "gmail",
  auth: {
    user: "seuemail@gmail.com",
    pass: "senha_do_app",
  },
});

const sendMail = async (to, subject, text, html, attachments) => {
  await transporter.sendMail({
      from: `"Suporte" email@gmail.com`,
      to,
      subject,
      text: text || undefined,
      html: finalHtml || undefined,
      attachments,
    });
}

module.exports = {
  sendMail,
};
```
