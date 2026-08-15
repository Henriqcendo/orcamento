# 🏗️ Orçamento de Obra

Aplicativo web interativo para cotação e comparação de materiais de construção entre múltiplos fornecedores.

## ✅ Funcionalidades

- 📱 **Mobile-first** — otimizado para celular
- 📝 **Edição inline** — clique em qualquer campo para editar
- 🏆 **Destaque automático** do menor preço por item e total
- ☁️ **Sincronização Firebase** em tempo real
- 🔗 **Link compartilhável** via URL única
- 📊 **Exportar para CSV** para abrir no Excel
- 🖨️ **Imprimir / Gerar PDF**
- 💾 **Salva localmente** (offline-first)

---

## ⚙️ Configuração do Firebase (para sincronização em nuvem)

### Passo 1 — Criar projeto Firebase

1. Acesse [console.firebase.google.com](https://console.firebase.google.com)
2. Clique em **"Adicionar projeto"**
3. Siga o assistente (Analytics é opcional)

### Passo 2 — Criar banco Firestore

1. No menu lateral, vá em **Build → Firestore Database**
2. Clique em **"Criar banco de dados"**
3. Escolha o modo **"Produção"** ou **"Teste"** (teste é mais fácil para começar)
4. Escolha a região mais próxima (ex: `southamerica-east1`)

### Passo 3 — Obter credenciais

1. Clique no ícone ⚙️ ao lado de "Visão geral do projeto"
2. Vá em **"Configurações do projeto"**
3. Role até **"Seus aplicativos"** → clique em **"Web"** (ícone `</>`)
4. Registre o app (nome qualquer)
5. Copie o objeto `firebaseConfig`

### Passo 4 — Inserir no `index.html`

Abra o `index.html` e localize o bloco:

```javascript
const FIREBASE_CONFIG = {
  apiKey:            "SUA_API_KEY_AQUI",
  authDomain:        "SEU_PROJETO.firebaseapp.com",
  projectId:         "SEU_PROJETO_ID",
  storageBucket:     "SEU_PROJETO.appspot.com",
  messagingSenderId: "SEU_SENDER_ID",
  appId:             "SEU_APP_ID"
};
```

Substitua pelos valores reais do seu projeto.

### Passo 5 — Regras de segurança (Firestore)

No console Firebase → **Firestore → Regras**, use para teste:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /orcamentos/{id} {
      allow read, write: if true;
    }
  }
}
```

> ⚠️ Para produção, adicione autenticação!

---

## 🌐 Deploy no GitHub Pages

### Passo 1 — Criar repositório

1. Vá em [github.com/new](https://github.com/new)
2. Nome sugerido: `orcamento-obra`
3. Marque como **Público**
4. Clique em **"Create repository"**

### Passo 2 — Enviar arquivos

```bash
cd "C:\Users\vlademir.henrique\Downloads\orçamento"
git init
git add .
git commit -m "feat: orçamento de obra"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/orcamento-obra.git
git push -u origin main
```

### Passo 3 — Ativar GitHub Pages

1. No repositório → **Settings → Pages**
2. Em **"Source"**, selecione `main` branch e pasta `/root`
3. Clique em **Save**
4. Aguarde ~2 minutos e acesse: `https://SEU_USUARIO.github.io/orcamento-obra`

---

## 📋 Como usar

| Ação | Como fazer |
|------|------------|
| Editar nome do item | Clique no campo e digite |
| Inserir preço | Clique na célula de preço e digite o valor |
| Adicionar item | Botão **➕ Novo Item** |
| Remover item | Botão **✕** na linha |
| Renomear fornecedor | Clique no nome do fornecedor no cabeçalho |
| Salvar | Botão **💾 Salvar** (ou aguarde salvar automático) |
| Compartilhar | Copie a URL (ela contém o ID único do seu orçamento) |
| Exportar Excel | Botão **📊 Exportar CSV** |

---

## 🛠️ Tecnologias

- **HTML5 + CSS3 + JavaScript** (sem dependências externas)
- **Firebase Firestore** v10 (CDN)
- **Google Fonts** — Inter
- **GitHub Pages** para hospedagem
