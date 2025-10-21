🚀 Challenge-Mobile-main: Plataforma de Análise Financeira XPEste projeto é uma aplicação móvel que simula o fluxo de autenticação e segurança de uma plataforma financeira, utilizando React Native, Expo Router e verificação biométrica facial obrigatória.🎯 Objetivo e Fluxo de SegurançaO objetivo principal é demonstrar um fluxo de Autenticação em Duas Etapas (2FA) forçada, garantindo que o usuário passe pela senha e, em seguida, pela biometria, antes de acessar os dados financeiros.Conexão do Reconhecimento Facial com o AplicativoO reconhecimento facial é o portão de acesso ao conteúdo principal e é orquestrado pelo Expo Router.Login (Senha) - Rota /login: Após o usuário inserir a senha com sucesso, o componente login.tsx utiliza o router.replace para forçar a navegação para a próxima etapa:TypeScript// No app/login.tsx
router.replace("/face-analysis");
Verificação Facial - Rota /face-analysis: Esta tela é a barreira final de segurança.O componente utiliza a Camera e o expo-face-detector para analisar o rosto em tempo real.O componente importa e chama a lógica de negócio identifyFace do serviço (../src/services/faceRecognitionService) para validar a biometria.Acesso ao Conteúdo Principal (Sucesso): Somente se a função identifyFace retornar sucesso, o usuário é autorizado a entrar no ambiente principal (/(tabs)), onde estão localizados os dados financeiros (como a Análise de PIX):TypeScript// No app/face-analysis.tsx
router.replace('/(tabs)');
🛠️ Tecnologias PrincipaisCategoriaTecnologiaVersão (Aproximada)Propósito no ProjetoRoteamentoExpo Router2.0.0Gerencia o fluxo de autenticação e define rotas públicas/privadas.LinguagemTypeScript (TSX)Utilizado nas rotas principais (login.tsx, face-analysis.tsx) e serviços (pixAnalysisService.ts) para tipagem segura.Biometriaexpo-camera, expo-face-detectorMódulos nativos para acesso à câmera e detecção facial em tempo real na rota /face-analysis.🏗️ Estrutura do ProjetoO projeto adota o padrão de rotas do Expo Router (file-system routing):Challenge-Mobile-main/
├── app/
│   ├── (tabs)/             # Rota Privada: Conteúdo principal (Ex: Análise PIX)
│   ├── face-analysis.tsx   # Rota Segura: Barreira Biometrica (Câmera)
│   └── login.tsx           # Rota Pública: Entrada por Senha
└── src/
    ├── services/           # Lógica de Negócio (identifyFace, pixAnalysisService)
    └── screens/            # Contém resquícios de arquivos JS legados (LoginScreen.js, etc.)
⚙️ Guia de Instalação e ExecuçãoPré-requisitosNode.js (LTS)npm ou pnpmExpo Go app (no seu dispositivo móvel)1. Instalação de DependênciasCertifique-se de que o seu terminal está no diretório raiz do projeto (Challenge-Mobile-main):Bash# 1. Instala as dependências (lendo o package.json)
npm install 

# 2. Garante que os módulos nativos (camera, face-detector) estejam presentes
npx expo install expo-camera expo-face-detector
2. Limpeza e InicializaçãoO sistema de rotas exige a limpeza do cache para reconhecer corretamente as rotas do app/.Bash# Inicia o Metro Bundler e limpa o cache
npx expo start --clear
Escaneie o QR Code com o Expo Go para carregar o aplicativo. O fluxo iniciará na tela de Login.
