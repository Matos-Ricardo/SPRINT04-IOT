🚀 Challenge-Mobile-main: Plataforma de Análise Financeira XPEste projeto simula o fluxo de autenticação e segurança (2FA) de uma plataforma financeira, utilizando React Native, Expo Router e verificação biométrica facial obrigatória.

KAYKY - 99756

FELIPE - 98595

PAULO - 551137

LEONARDO - 99902

RICARDO - 95906

🛡️ Objetivo e Fluxo de SegurançaO objetivo é implementar e demonstrar um fluxo de Autenticação em Duas Etapas (2FA) forçada, garantindo que o usuário passe pela senha e, em seguida, pela biometria, antes de acessar o conteúdo principal.Conexão do Reconhecimento Facial 

🤳O reconhecimento facial atua como o portão de acesso obrigatório.Login (Senha) - Rota /login: Após o sucesso da senha, o componente login.tsx força o redirecionamento para a biometria:TypeScript// No app/login.tsx 

router.replace("/face-analysis"); Verificação Facial - Rota /face-analysis: Esta tela é a barreira de segurança. Ela usa a Camera e o expo-face-detector para analisar o rosto em tempo real. O componente chama a lógica de negócio (../src/services/faceRecognitionService) para validar a biometria.Acesso ao Conteúdo Principal (Sucesso): Apenas se a validação facial for bem-sucedida, o usuário é liberado para o ambiente principal (/(tabs)):TypeScript// No app/face-analysis.tsx
router.replace('/(tabs)');

🛠️ Tecnologias PrincipaisCategoriaTecnologiaPropósito no ProjetoRoteamentoExpo RouterGerencia o fluxo de autenticação e define rotas públicas/privadas.LinguagemTypeScript (TSX)Adiciona tipagem segura às rotas (login.tsx, face-analysis.tsx) e serviços.Biometriaexpo-camera, expo-face-detectorMódulos nativos para detecção facial em tempo real na rota /face-analysis.🏗️ Estrutura do ProjetoO projeto adota o padrão de rotas do Expo Router (file-system routing):

Challenge-Mobile-main/
├── app/
│   ├── (tabs)/             # Rota Privada: Conteúdo principal (Ex: Análise PIX)
│   ├── face-analysis.tsx   # Rota Segura: Barreira Biometrica (Câmera)
│   └── login.tsx           # Rota Pública: Entrada por Senha
└── src/
    ├── services/           # Lógica de Negócio (identifyFace, pixAnalysisService)
    └── screens/            # Contém arquivos JS legados (serão removidos)
    
⚙️ Guia de Instalação e Execução 🏁Pré-requisitosNode.js (LTS)npm ou pnpmExpo Go app (no seu dispositivo móvel)1. Instalação de DependênciasCertifique-se de que o seu terminal está no diretório raiz do projeto:Bash# 1. Instala as dependências (lendo o package.json)
npm install 

# 2. Garante que os módulos nativos (camera, face-detector) estejam presentes
npx expo install expo-camera expo-face-detector
2. Limpeza e InicializaçãoÉ crucial limpar o cache do Expo para reconhecer corretamente as rotas e módulos nativos:Bash# Inicia o Metro Bundler e limpa o cache

npx expo start --clear

Escaneie o QR Code com o Expo Go para carregar o aplicativo. O fluxo iniciará na tela de Login.
