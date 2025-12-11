# Game-Architect-Agent
<div align="center">

# 🎮 Game-Architect-Agent

### Votre co-pilote IA pour la conception de jeux vidéo.
**Un agent autonome capable de brainstormer des mécaniques, d'inventer du lore et de valider des concepts grâce à des données réelles.**

<p>
  <img src="https://img.shields.io/badge/Built%20with-n8n-FF6F61?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n">
  <img src="https://img.shields.io/badge/AI%20Engine-Groq%20%2F%20Llama3-F05032?style=for-the-badge&logo=fastapi&logoColor=white" alt="Groq">
  <img src="https://img.shields.io/badge/Architecture-RAG%20Agent-blueviolet?style=for-the-badge" alt="RAG">
  <img src="https://img.shields.io/badge/Tools-Wikipedia%20%26%20Memory-informational?style=for-the-badge" alt="Tools">
</p>

[Voir la démo](#-exemple-dutilisation) • [Comment ça marche ?](#%EF%B8%8F-architecture-technique) • [Installation](#-installation-et-utilisation)

</div>

---

## 📰 À propos du projet

Dans le développement de jeux vidéo, la phase de pré-production est cruciale. Le **Game-Architect-Agent** a été conçu pour accélérer cette phase créative.

Ce n'est pas un simple chatbot. C'est un **Agent Autonome** spécialisé, programmé avec un "System Prompt" d'expert en Game Design. Il agit comme un partenaire de brainstorming capable de :
1.  Proposer des boucles de gameplay (Core Loops) innovantes.
2.  Maintenir le contexte d'un projet sur le long terme grâce à sa mémoire.
3.  **Utiliser des outils externes** (comme Wikipédia) pour ancrer les concepts dans la réalité (physique, histoire, phénomènes naturels).

Ce projet démontre l'application concrète de l'**Ingénierie IA** au service de l'industrie créative.

---

## ✨ Fonctionnalités Clés

| Fonctionnalité | Description Technique |
| :--- | :--- |
| **🧠 Cerveau Ultra-Rapide** | Propulsé par **Llama 3 (70B)** via l'infrastructure LPU de **Groq** pour une inférence quasi-instantanée. |
| **📚 Recherche Autonome (RAG)** | Capacité d'utiliser l'outil **Wikipédia** de manière autonome pour rechercher des faits techniques ou historiques si sa connaissance interne ne suffit pas. |
| **💬 Mémoire Contextuelle** | Utilisation d'un **Window Buffer Memory** pour se souvenir des détails du projet (titre, genre, contraintes) au fil de la conversation. |
| **🎭 Persona Expert** | Un *System Prompt* finement calibré pour forcer l'IA à adopter une posture de Game Designer senior, structuré et technique. |

---

## 🏗️ Architecture Technique

Ce projet est construit sur une architecture **Low-Code** robuste utilisant **n8n**.

```mermaid
graph TD;
    User(Utilisateur / Game Designer) -->|Prompt via Chat| ChatTrigger;
    subgraph n8n Workflow
        ChatTrigger --> AI_Agent[🤖 AI Agent Node];
        AI_Agent <-->|Inférence Rapide| Groq(🧠 Model: Groq / Llama 3);
        AI_Agent <-->|Stockage Contexte| Memory(💾 Window Buffer Memory);
        AI_Agent -->|Si besoin d'info externe| Wikipedia(📚 Tool: Wikipedia Search);
        Wikipedia -->|Retourne l'article| AI_Agent;
    end
    AI_Agent -->|Concept Structuré| Output(Réponse dans le Chat);
    style AI_Agent fill:#f9f,stroke:#333,stroke-width:2px,color:#000
    style Groq fill:#ff9980,stroke:#f66,stroke-width:2px,color:#000

    L'agent central orchestre les décisions : doit-il répondre avec sa connaissance interne, ou doit-il déclencher l'outil Wikipédia avant de formuler sa réponse ?

🎯 Exemple d'utilisation
Scénario : Le designer cherche une mécanique sonore réaliste pour un jeu dans le désert.

Utilisateur : "Pour rendre le jeu réaliste, je veux m'inspirer d'un vrai phénomène. Cherche sur Wikipédia ce qu'est le 'Chant des dunes' et propose-moi une mécanique de jeu sonore basée là-dessus."

Réponse de l'Agent (après utilisation autonome de l'outil Wikipédia) :

"Sur la base de l'article de Wikipédia, le 'Chant des dunes' est un phénomène acoustique où le sable émet un son grave...

Proposition de Mécanique : Le Sonar des Sables Le joueur doit écouter la fréquence du sable. Un son grave et continu indique une dune stable. Un son qui devient aigu ou saccadé signale une avalanche imminente ou la présence d'une créature fouisseuse..."

🚀 Installation et Utilisation
Ce projet est un workflow n8n. Pour l'utiliser, vous devez avoir une instance n8n locale (via Docker recommandé).

Prérequis
Docker installé.

Une clé API gratuite sur Groq Console.

Étapes
Clonez ce dépôt.

Lancez votre instance n8n :

Bash

docker run -it --rm --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n
Accédez à http://localhost:5678.

Dans n8n, créez un nouveau workflow, cliquez sur le menu en haut à droite > "Import from File".

Sélectionnez le fichier workflow.json présent dans ce dépôt.

Configurez vos identifiants Groq dans le nœud correspondant.

Lancez le Chat et commencez à créer !

<div align="center">

Développé avec passion par Aminata Sané Architecte d'Intelligences : Jeu Vidéo, Immersion & Agents Autonomes

</div>
