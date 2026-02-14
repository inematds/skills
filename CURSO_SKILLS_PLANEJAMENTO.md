# CURSO COMPLETO: Agent Skills para IA

> **Domine a criacao de Skills para agentes de IA**
> **Versao:** 2.0 | **Data:** 2026-02-14

---

## VISAO GERAL DO CURSO

| Item | Valor |
|------|-------|
| Nome | Agent Skills Mastery |
| Emoji | `🧠` |
| Total de Trilhas | 6 |
| Total de Modulos | 48 |
| Topicos por Modulo | 6-8 |
| Total Estimado de Topicos | ~300 |

---

## ESTRUTURA DAS 6 TRILHAS

| Trilha | Nome | Cor | Foco | Modulos |
|--------|------|-----|------|---------|
| T1 | Fundamentos | Emerald | Conceitos, estrutura SKILL.md, especificacao | 8 |
| T2 | Claude Code | Blue | Anthropic, Claude.ai, Claude API | 8 |
| T3 | AntiGravity & Gemini | Purple | Gemini CLI, AntiGravity, Stitch Skills | 8 |
| T4 | Ecossistema | Amber | Superpowers, comunidade, marketplaces | 8 |
| T5 | Skills Universal | Cyan | Padrao universal, Copilot, Cursor, Manus, Cline, Codex | 8 |
| T6 | Exemplos & Aplicacoes | Rose | Repositorios reais, colecoes awesome, multi-agent, marketplaces | 8 |

---

# TRILHA 1: FUNDAMENTOS (Emerald)

> **O que sao Skills e como funcionam**

## Modulo 1.1 - Introducao a Agent Skills

**Duracao:** ~35 min | **Nivel:** Iniciante

### Topicos:

1. **🎯 O que sao Agent Skills**
   - **O que e:** Capacidades modulares e reutilizaveis que estendem a funcionalidade de agentes de IA
   - **Por que aprender:** Skills transformam agentes generalistas em especialistas sem repetir instrucoes
   - **Conceitos-chave:** Modularidade, descoberta dinamica, reutilizacao, baseado em arquivos

2. **🔄 Skills vs Tools vs Prompts**
   - **O que e:** Distincao entre o que agentes SABEM (skills) e o que PODEM FAZER (tools)
   - **Por que aprender:** Entender quando usar cada abordagem maximiza eficiencia
   - **Conceitos-chave:** Skills = conhecimento, Tools = acoes, Prompts = instrucoes unicas

3. **📦 Anatomia de uma Skill**
   - **O que e:** Estrutura basica: pasta com SKILL.md + recursos opcionais
   - **Por que aprender:** Saber a estrutura permite criar skills validas desde o inicio
   - **Conceitos-chave:** SKILL.md, frontmatter YAML, corpo Markdown

4. **🌐 Ecossistema de Skills**
   - **O que e:** Panorama dos players: Anthropic, Google, comunidade open-source
   - **Por que aprender:** Conhecer opcoes permite escolher a melhor para cada caso
   - **Conceitos-chave:** agentskills.io, repositorios oficiais, marketplaces

5. **💡 Casos de Uso Reais**
   - **O que e:** Exemplos praticos: documentos, TDD, debugging, branding, analytics
   - **Por que aprender:** Inspiracao para criar skills proprias baseadas em necessidades reais
   - **Conceitos-chave:** Document skills, Development skills, Enterprise skills

6. **🚀 Primeiros Passos**
   - **O que e:** Como comecar: instalar skills existentes vs criar do zero
   - **Por que aprender:** Ter um roadmap claro acelera o aprendizado
   - **Conceitos-chave:** Diretorio ~/.claude/skills/, .claude/skills/ (projeto)

### Recursos:
- [AgentSkills.io - Overview](https://agentskills.io/home)
- [Anthropic Skills Blog](https://anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)
- [Simon Willison - Skills are awesome](https://simonwillison.net/2025/Oct/16/claude-skills/)

---

## Modulo 1.2 - Estrutura do Arquivo SKILL.md

**Duracao:** ~40 min | **Nivel:** Iniciante

### Topicos:

1. **📄 O Arquivo SKILL.md**
   - **O que e:** Arquivo principal que define a skill - "controle de missao" para o agente
   - **Por que aprender:** E o unico arquivo OBRIGATORIO em qualquer skill
   - **Conceitos-chave:** Markdown, frontmatter, instrucoes

2. **🏷️ Frontmatter YAML - name**
   - **O que e:** Campo obrigatorio que identifica a skill (max 64 chars)
   - **Por que aprender:** Nome mal formatado impede a skill de ser descoberta
   - **Conceitos-chave:** lowercase, hyphens, sem "claude"/"anthropic"

   ```yaml
   ---
   name: sales-data-analyzer
   ---
   ```

3. **📝 Frontmatter YAML - description**
   - **O que e:** Campo obrigatorio que define QUANDO usar a skill (max 1024 chars)
   - **Por que aprender:** O agente usa a description para decidir se invoca a skill
   - **Conceitos-chave:** Terceira pessoa, triggers especificos, keywords

   ```yaml
   description: Analyzes sales CSV files and generates reports. Use when user mentions revenue analysis, sales data, or e-commerce metrics.
   ```

4. **🔧 Frontmatter YAML - allowed-tools**
   - **O que e:** Campo opcional que especifica quais ferramentas a skill pode usar
   - **Por que aprender:** Controle de seguranca e permissoes
   - **Conceitos-chave:** Bash, Read, Write, patterns com wildcard

   ```yaml
   allowed-tools: Bash(date:*), Read, Write
   ```

5. **📖 Corpo do Markdown - Estrutura**
   - **O que e:** Instrucoes que o agente segue quando a skill e invocada
   - **Por que aprender:** Instrucoes claras = resultados previsíveis
   - **Conceitos-chave:** Sections, headings, bullet points, code blocks

6. **✅ Exemplo Completo Comentado**
   - **O que e:** Skill funcional linha por linha explicada
   - **Por que aprender:** Ver exemplo real consolida o aprendizado
   - **Conceitos-chave:** Template replicavel

   ```yaml
   ---
   name: timestamp-generator
   description: Creates timestamps for files and directories. Use when user needs to add dates to filenames or organize files by date.
   allowed-tools: Bash(date:*)
   ---

   # Timestamp Generator

   ## When to Use
   - User asks to timestamp a file
   - User wants date-based organization
   - User mentions "add date to filename"

   ## Instructions
   1. Use format: YYYY-MM-DD-HH-MM-SS
   2. Apply to files, directories, or other resources
   3. Use Bash date command for accuracy

   ## Example
   Input: report.pdf
   Output: 2026-02-04-14-30-00-report.pdf
   ```

### Recursos:
- [Agent Skills Specification](https://agentskills.io/specification)
- [What Is SKILL.md](https://skywork.ai/blog/ai-agent/claude-skills-skill-md-resources-runtime-loading/)

---

## Modulo 1.3 - Estrutura de Diretorios

**Duracao:** ~30 min | **Nivel:** Iniciante

### Topicos:

1. **📁 Hierarquia Padrao**
   - **O que e:** Estrutura de pastas recomendada para skills
   - **Por que aprender:** Organizacao correta facilita manutencao e compartilhamento
   - **Conceitos-chave:** SKILL.md, scripts/, examples/, resources/

   ```
   skill-name/
   ├── SKILL.md          # Obrigatorio
   ├── scripts/          # Opcional - helpers
   ├── examples/         # Opcional - referencias
   └── resources/        # Opcional - templates, assets
   ```

2. **🏠 Skills Globais (~/.claude/skills/)**
   - **O que e:** Skills disponiveis em TODOS os projetos do usuario
   - **Por que aprender:** Ideal para skills de uso geral (code review, TDD, etc.)
   - **Conceitos-chave:** Diretorio home, persistencia, compartilhamento

3. **📂 Skills de Projeto (.claude/skills/)**
   - **O que e:** Skills especificas de um projeto/repositorio
   - **Por que aprender:** Perfeito para convencoes de time, workflows especificos
   - **Conceitos-chave:** Raiz do projeto, versionamento, contexto local

4. **📜 Pasta scripts/**
   - **O que e:** Scripts auxiliares (Python, Bash, Node) chamados pela skill
   - **Por que aprender:** Automatiza tarefas complexas mantendo SKILL.md limpo
   - **Conceitos-chave:** Executaveis, validacao, automacao

5. **📚 Pasta resources/**
   - **O que e:** Templates, JSON de configuracao, assets estaticos
   - **Por que aprender:** Centraliza dados que a skill referencia
   - **Conceitos-chave:** design-tokens.json, templates, checklists

6. **💡 Pasta examples/**
   - **O que e:** Implementacoes de referencia, casos de uso documentados
   - **Por que aprender:** Exemplos ajudam o agente a entender o padrao esperado
   - **Conceitos-chave:** Golden examples, patterns, anti-patterns

### Exemplo Pratico - Brand Identity Skill:

```
brand-identity/
├── SKILL.md                    # Router principal
└── resources/
    ├── design-tokens.json      # Cores, fontes, espacamentos
    ├── tech-stack.md           # React, Tailwind, shadcn/ui
    └── voice-tone.md           # Tom de voz da marca
```

---

## Modulo 1.4 - Escrevendo Instrucoes Eficazes

**Duracao:** ~45 min | **Nivel:** Intermediario

### Topicos:

1. **✍️ Principios de Escrita (The Claude Way)**
   - **O que e:** Best practices para escrever instrucoes que agentes entendem
   - **Por que aprender:** Instrucoes ruins = resultados imprevisiveis
   - **Conceitos-chave:** Concisao, clareza, especificidade

2. **📏 Regra dos 500 Lines**
   - **O que e:** SKILL.md deve ter menos de 500 linhas
   - **Por que aprender:** Previne sobrecarga de contexto
   - **Conceitos-chave:** Progressive disclosure, arquivos secundarios

3. **🎚️ Graus de Liberdade**
   - **O que e:** Quando usar bullets, code blocks ou comandos exatos
   - **Por que aprender:** Controle fino sobre o comportamento do agente
   - **Conceitos-chave:**
     - **Bullet Points** = Alta liberdade (heuristicas)
     - **Code Blocks** = Media liberdade (templates)
     - **Comandos Bash** = Baixa liberdade (operacoes frageis)

4. **🔗 Progressive Disclosure**
   - **O que e:** Tecnica de revelar informacao gradualmente
   - **Por que aprender:** Mantem SKILL.md enxuto, detalhes em arquivos separados
   - **Conceitos-chave:** Links para ADVANCED.md, apenas 1 nivel de profundidade

5. **📋 Checklists e Validacao**
   - **O que e:** Listas de verificacao que o agente pode copiar e atualizar
   - **Por que aprender:** Permite tracking de estado em tarefas complexas
   - **Conceitos-chave:** Markdown checkboxes, estado mutavel

   ```markdown
   ## Deployment Checklist
   - [ ] Run tests
   - [ ] Check environment variables
   - [ ] Verify database migrations
   - [ ] Deploy to staging
   - [ ] Smoke test
   - [ ] Deploy to production
   ```

6. **⚠️ Tratamento de Erros**
   - **O que e:** Como instruir o agente a lidar com falhas
   - **Por que aprender:** Skills robustas precisam de fallbacks
   - **Conceitos-chave:** Black box scripts, --help, mensagens de erro claras

### Recursos:
- [How to Make Skills Activate Reliably](https://scottspence.com/posts/how-to-make-claude-code-skills-activate-reliably)

---

## Modulo 1.5 - Descriptions que Ativam

**Duracao:** ~35 min | **Nivel:** Intermediario

### Topicos:

1. **🎯 A Importancia da Description**
   - **O que e:** O campo description e o "gatilho" que decide se a skill e invocada
   - **Por que aprender:** Description ruim = skill nunca ativada
   - **Conceitos-chave:** Matching, relevancia, triggers

2. **❌ Erros Comuns**
   - **O que e:** Descriptions vagas, genericas ou muito curtas
   - **Por que aprender:** Evitar armadilhas comuns economiza tempo de debug
   - **Conceitos-chave:**

   ```yaml
   # RUIM - muito vago
   description: Helps with code

   # RUIM - nao diz QUANDO usar
   description: A tool for data analysis
   ```

3. **✅ Padrao Eficaz**
   - **O que e:** Formula: O QUE faz + QUANDO usar + KEYWORDS
   - **Por que aprender:** Descriptions bem estruturadas ativam consistentemente
   - **Conceitos-chave:**

   ```yaml
   # BOM - especifico e com triggers
   description: Analyzes e-commerce sales data from CSV or Excel files, generates visualizations, identifies trends, and creates executive summary reports. Use when user mentions sales data, revenue analysis, Shopify, e-commerce metrics, order data, or wants insights from transactional data.
   ```

4. **🔑 Keywords Estrategicas**
   - **O que e:** Palavras que usuarios provavelmente usarao
   - **Por que aprender:** Keywords certas aumentam taxa de ativacao
   - **Conceitos-chave:** Sinonimos, jargao do dominio, acoes comuns

5. **📊 Testando Ativacao**
   - **O que e:** Como verificar se a skill esta sendo descoberta
   - **Por que aprender:** Debug de ativacao evita frustracoes
   - **Conceitos-chave:** Logs, prompts de teste, iteracao

6. **🎨 Exemplos por Dominio**
   - **O que e:** Descriptions otimizadas para diferentes areas
   - **Por que aprender:** Templates prontos para adaptar
   - **Conceitos-chave:**

   ```yaml
   # Development
   description: Runs test-driven development workflow with RED-GREEN-REFACTOR cycle. Use when user wants to write tests first, mentions TDD, or asks for test coverage.

   # Documents
   description: Creates PowerPoint presentations from outlines or data. Use when user mentions slides, presentation, pptx, or wants to generate a deck.

   # Analytics
   description: Performs customer health analysis and churn prediction. Use when user mentions customer scoring, retention risk, or health metrics.
   ```

---

## Modulo 1.6 - Recursos e Scripts

**Duracao:** ~40 min | **Nivel:** Intermediario

### Topicos:

1. **📁 Quando Usar Recursos Externos**
   - **O que e:** Criterios para adicionar scripts/, examples/, resources/
   - **Por que aprender:** Nem toda skill precisa de arquivos extras
   - **Conceitos-chave:** Complexidade, reutilizacao, separacao de concerns

2. **🐍 Scripts Python**
   - **O que e:** Scripts auxiliares para processamento de dados, APIs, etc.
   - **Por que aprender:** Python e ideal para tarefas de automacao
   - **Conceitos-chave:** pandas, requests, openpyxl

   ```python
   # scripts/analyze_data.py
   import pandas as pd
   import sys

   def analyze(filepath):
       df = pd.read_csv(filepath)
       summary = df.describe()
       print(summary.to_markdown())

   if __name__ == "__main__":
       analyze(sys.argv[1])
   ```

3. **🔧 Scripts Bash**
   - **O que e:** Automacao de tarefas de sistema, git, deploy
   - **Por que aprender:** Shell scripts sao universais e rapidos
   - **Conceitos-chave:** Validacao, setup, cleanup

   ```bash
   #!/bin/bash
   # scripts/validate_env.sh

   required_vars=("API_KEY" "DATABASE_URL" "NODE_ENV")

   for var in "${required_vars[@]}"; do
       if [ -z "${!var}" ]; then
           echo "ERROR: $var is not set"
           exit 1
       fi
   done

   echo "Environment validated successfully"
   ```

4. **📋 JSON de Configuracao**
   - **O que e:** Arquivos JSON para tokens de design, configuracoes, dados
   - **Por que aprender:** Agentes preferem JSON para valores exatos
   - **Conceitos-chave:** design-tokens.json, config.json

   ```json
   {
     "colors": {
       "primary": "#FACC15",
       "secondary": "#1E40AF",
       "background": "#111827"
     },
     "typography": {
       "font_family": ["Inter", "sans-serif"],
       "font_size_base": "16px"
     }
   }
   ```

5. **📝 Templates Markdown**
   - **O que e:** Templates que o agente preenche (PR, commits, docs)
   - **Por que aprender:** Padronizacao de outputs
   - **Conceitos-chave:** Placeholders, estrutura, exemplos

6. **🔗 Referenciando Recursos no SKILL.md**
   - **O que e:** Como linkar para arquivos de recursos
   - **Por que aprender:** Links corretos garantem que o agente encontra os arquivos
   - **Conceitos-chave:**

   ```markdown
   ## Resources
   - Design tokens: [`resources/design-tokens.json`](resources/design-tokens.json)
   - Tech stack rules: [`resources/tech-stack.md`](resources/tech-stack.md)
   ```

---

## Modulo 1.7 - Boas Praticas e Seguranca

**Duracao:** ~35 min | **Nivel:** Intermediario

### Topicos:

1. **🔒 Nunca Inclua Secrets**
   - **O que e:** API keys, senhas, tokens NUNCA devem estar em skills
   - **Por que aprender:** Vazamento de credenciais e risco critico
   - **Conceitos-chave:** .env, variaveis de ambiente

   ```markdown
   ## Configuration
   Use the API key from environment variable $API_KEY
   Never hardcode credentials in this skill
   ```

2. **📏 Mantenha Conciso**
   - **O que e:** Menos e mais - assuma que o agente e inteligente
   - **Por que aprender:** Instrucoes longas demais confundem
   - **Conceitos-chave:** Nao explique o obvio, foque na logica unica

3. **🧪 Teste Incrementalmente**
   - **O que e:** Teste skills em tarefas pequenas antes de projetos grandes
   - **Por que aprender:** Debug mais facil, iteracao rapida
   - **Conceitos-chave:** MVP skill, feedback loop

4. **📚 Documente Limitacoes**
   - **O que e:** Seja transparente sobre o que a skill NAO faz
   - **Por que aprender:** Evita expectativas erradas
   - **Conceitos-chave:** Limitacoes, edge cases, pre-requisitos

5. **🔄 Versionamento**
   - **O que e:** Controle de versao de skills (git, changelogs)
   - **Por que aprender:** Facilita rollback e colaboracao
   - **Conceitos-chave:** Semantic versioning, CHANGELOG.md

6. **✅ Checklist de Qualidade**
   - **O que e:** Verificacao antes de publicar uma skill
   - **Por que aprender:** Garante qualidade consistente
   - **Conceitos-chave:**

   ```markdown
   ## Quality Checklist
   - [ ] name usa lowercase-with-hyphens
   - [ ] description inclui WHAT + WHEN + KEYWORDS
   - [ ] SKILL.md < 500 linhas
   - [ ] Sem secrets hardcoded
   - [ ] Testada em cenarios variados
   - [ ] Recursos linkados corretamente
   ```

---

## Modulo 1.8 - Especificacao Oficial

**Duracao:** ~30 min | **Nivel:** Avancado

### Topicos:

1. **📜 AgentSkills.io Specification**
   - **O que e:** Especificacao oficial mantida pela comunidade
   - **Por que aprender:** Garante interoperabilidade entre plataformas
   - **Conceitos-chave:** Open standard, Anthropic, Google, comunidade

2. **🔧 Campos do Frontmatter**
   - **O que e:** Todos os campos possiveis no YAML
   - **Por que aprender:** Conhecer opcoes avancadas
   - **Conceitos-chave:** name, description, allowed-tools, version

3. **📱 Compatibilidade Cross-Platform**
   - **O que e:** Skills funcionam em Claude, Gemini, Cursor, etc.
   - **Por que aprender:** Criar skills portaveis e mais valioso
   - **Conceitos-chave:** Formato universal, agnostico de plataforma

4. **🔄 Ciclo de Vida da Skill**
   - **O que e:** Discovery -> Loading -> Execution -> Cleanup
   - **Por que aprender:** Entender o fluxo ajuda no debug
   - **Conceitos-chave:** Invocacao, contexto, estado

5. **📊 Metricas e Observabilidade**
   - **O que e:** Como monitorar uso e performance de skills
   - **Por que aprender:** Melhoria continua baseada em dados
   - **Conceitos-chave:** Logs, metricas, feedback

6. **🌐 Contribuindo para o Padrao**
   - **O que e:** Como propor mudancas na especificacao
   - **Por que aprender:** Participar da evolucao do ecossistema
   - **Conceitos-chave:** GitHub, PRs, discussoes

### Recursos:
- [AgentSkills Specification](https://agentskills.io/specification)
- [GitHub - agentskills/agentskills](https://github.com/agentskills/agentskills)

---

# TRILHA 2: CLAUDE CODE (Blue)

> **Skills para o ecossistema Anthropic**

## Modulo 2.1 - Introducao ao Claude Code Skills

**Duracao:** ~35 min | **Nivel:** Iniciante

### Topicos:

1. **🤖 O que e Claude Code**
   - **O que e:** CLI oficial da Anthropic para desenvolvimento com Claude
   - **Por que aprender:** Plataforma principal para skills de coding
   - **Conceitos-chave:** Terminal, IDE integration, agentic coding

2. **📦 Repositorio Oficial anthropics/skills**
   - **O que e:** Colecao oficial de skills da Anthropic (62.9k stars)
   - **Por que aprender:** Fonte autoritativa, exemplos de referencia
   - **Conceitos-chave:** Apache 2.0, document skills, template

3. **💾 Instalando Skills Oficiais**
   - **O que e:** Comando para clonar e instalar skills oficiais
   - **Por que aprender:** Comecar rapidamente com skills prontas
   - **Conceitos-chave:**

   ```bash
   git clone --depth 1 https://github.com/anthropics/skills.git /tmp/anthropic-skills && \
   mkdir -p .claude/skills && \
   cp -r /tmp/anthropic-skills/skills/*/ .claude/skills/ && \
   rm -rf /tmp/anthropic-skills
   ```

4. **🔌 Plugin Marketplace**
   - **O que e:** Sistema de plugins do Claude Code
   - **Por que aprender:** Instalacao simplificada via marketplace
   - **Conceitos-chave:**

   ```bash
   /plugin marketplace add anthropics/skills
   /plugin install document-skills@anthropic-agent-skills
   ```

5. **📂 Estrutura de Diretorios**
   - **O que e:** Onde colocar skills no Claude Code
   - **Por que aprender:** Local correto garante descoberta
   - **Conceitos-chave:**
     - Global: `~/.claude/skills/`
     - Projeto: `.claude/skills/`

6. **🎯 Skills Incluidas**
   - **O que e:** Skills oficiais: xlsx, pptx, docx, pdf
   - **Por que aprender:** Saber o que ja existe evita retrabalho
   - **Conceitos-chave:** Document generation, Office formats

### Recursos:
- [GitHub - anthropics/skills](https://github.com/anthropics/skills)
- [Claude Code Docs - Skills](https://code.claude.com/docs/en/skills)

---

## Modulo 2.2 - Document Skills (Office)

**Duracao:** ~45 min | **Nivel:** Intermediario

### Topicos:

1. **📊 Skill xlsx (Excel)**
   - **O que e:** Criacao e manipulacao de planilhas Excel
   - **Por que aprender:** Automacao de relatorios e dados
   - **Conceitos-chave:** openpyxl, formulas, formatacao

2. **📑 Skill pptx (PowerPoint)**
   - **O que e:** Geracao de apresentacoes automatizadas
   - **Por que aprender:** Criar decks a partir de dados/outlines
   - **Conceitos-chave:** python-pptx, slides, layouts

3. **📝 Skill docx (Word)**
   - **O que e:** Geracao de documentos Word formatados
   - **Por que aprender:** Relatorios, contratos, documentacao
   - **Conceitos-chave:** python-docx, estilos, templates

4. **📄 Skill pdf**
   - **O que e:** Processamento e criacao de PDFs
   - **Por que aprender:** Formato universal de documentos
   - **Conceitos-chave:** reportlab, PyPDF2, extraction

5. **🔄 Workflow Integrado**
   - **O que e:** Combinar skills para pipelines de documentos
   - **Por que aprender:** Automacao end-to-end
   - **Conceitos-chave:** CSV -> Analise -> Excel + PDF + PPT

6. **💡 Exemplos Praticos**
   - **O que e:** Casos de uso reais com codigo
   - **Por que aprender:** Templates para adaptar
   - **Conceitos-chave:**

   ```python
   # Exemplo: Gerar relatorio de vendas
   import pandas as pd
   from openpyxl import Workbook

   df = pd.read_csv('sales.csv')
   summary = df.groupby('product')['revenue'].sum()

   wb = Workbook()
   ws = wb.active
   for idx, (product, revenue) in enumerate(summary.items(), 1):
       ws.cell(row=idx, column=1, value=product)
       ws.cell(row=idx, column=2, value=revenue)
   wb.save('sales_report.xlsx')
   ```

---

## Modulo 2.3 - Skills Generator (Meta-Skill)

**Duracao:** ~40 min | **Nivel:** Intermediario

### Topicos:

1. **🏭 O que e um Skills Generator**
   - **O que e:** Prompt/skill que gera outras skills automaticamente
   - **Por que aprender:** Acelera criacao de skills customizadas
   - **Conceitos-chave:** Meta-prompt, templates, automacao

2. **📋 Estrutura de Output**
   - **O que e:** O que o generator deve produzir
   - **Por que aprender:** Garantir pacotes completos
   - **Conceitos-chave:**
     - SKILL.md
     - demo-prompt.txt
     - SETUP.md
     - Sample data files
     - ZIP package

3. **📝 Template SKILL.md**
   - **O que e:** Modelo padrao para skills geradas
   - **Por que aprender:** Consistencia em todas as skills
   - **Conceitos-chave:** What, When, How, Example

4. **🎯 Variables de Input**
   - **O que e:** Parametros para customizar a skill gerada
   - **Por que aprender:** Flexibilidade na geracao
   - **Conceitos-chave:**
     - SKILL_TYPE (obrigatorio)
     - NUM_SKILLS (opcional)
     - COMPANY_CONTEXT (opcional)
     - BRAND_COLORS (opcional)

5. **✅ Quality Checklist Automatico**
   - **O que e:** Verificacoes que o generator executa
   - **Por que aprender:** Garante qualidade consistente
   - **Conceitos-chave:**

   ```markdown
   ## Quality Checklist
   - [ ] name usa lowercase-with-hyphens
   - [ ] description inclui WHAT + WHEN + KEYWORDS
   - [ ] Python code e completo e executavel
   - [ ] Sample data e realista
   - [ ] SETUP.md tem instrucoes para todas plataformas
   ```

6. **💡 Exemplo de Uso**
   - **O que e:** Como invocar o generator
   - **Por que aprender:** Uso pratico imediato
   - **Conceitos-chave:**

   ```
   SKILL_TYPE: Create a skill that analyzes customer feedback and generates sentiment reports
   NUM_SKILLS: 2
   COMPANY_CONTEXT: SaaS B2B company
   BRAND_COLORS: #6366F1, #10B981
   ```

### Recursos:
- [doc/cc/SKILL_GENERATOR_PROMPT.md](doc/cc/SKILL_GENERATOR_PROMPT.md)

---

## Modulo 2.4 - Claude.ai Skills

**Duracao:** ~35 min | **Nivel:** Intermediario

### Topicos:

1. **🌐 Skills no Claude.ai (Browser)**
   - **O que e:** Como usar skills na interface web do Claude
   - **Por que aprender:** Disponivel para usuarios nao-tecnicos
   - **Conceitos-chave:** Settings, Capabilities, Upload

2. **📤 Upload de Skills**
   - **O que e:** Processo de carregar skills customizadas
   - **Por que aprender:** Compartilhar skills com a equipe
   - **Conceitos-chave:**
     1. Baixar pasta da skill como ZIP
     2. Ir para Settings -> Capabilities
     3. Clicar "Upload Skill" e selecionar ZIP

3. **💳 Planos e Disponibilidade**
   - **O que e:** Skills disponiveis em planos pagos
   - **Por que aprender:** Entender limitacoes por tier
   - **Conceitos-chave:** Free, Pro, Team, Enterprise

4. **🔄 Sincronizacao com Projetos**
   - **O que e:** Como skills se relacionam com Projects
   - **Por que aprender:** Organizacao por contexto
   - **Conceitos-chave:** Project-specific skills

5. **📊 Skills Pre-Construidas**
   - **O que e:** Skills ja disponiveis no Claude.ai
   - **Por que aprender:** Usar antes de criar do zero
   - **Conceitos-chave:** Document skills, analysis skills

6. **🔗 Integracao com MCP**
   - **O que e:** Como Skills trabalham com Model Context Protocol
   - **Por que aprender:** Skills + MCP = poder combinado
   - **Conceitos-chave:** MCP para dados, Skills para logica

### Recursos:
- [Using Skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- [How to create custom Skills](https://support.claude.com/en/articles/12512198-how-to-create-custom-skills)

---

## Modulo 2.5 - Claude API Skills

**Duracao:** ~40 min | **Nivel:** Avancado

### Topicos:

1. **🔌 API de Skills**
   - **O que e:** Endpoint `/v1/skills` para upload programatico
   - **Por que aprender:** Integracao em pipelines e sistemas
   - **Conceitos-chave:** REST API, authentication, endpoints

2. **📦 Upload via API**
   - **O que e:** Como enviar skills programaticamente
   - **Por que aprender:** Automacao de deploy de skills
   - **Conceitos-chave:**

   ```python
   import anthropic

   client = anthropic.Anthropic()

   with open("skill.zip", "rb") as f:
       response = client.skills.upload(file=f)

   print(response.skill_id)
   ```

3. **📋 Listando Skills**
   - **O que e:** Recuperar skills disponiveis
   - **Por que aprender:** Gerenciamento programatico
   - **Conceitos-chave:**

   ```python
   skills = client.skills.list()
   for skill in skills:
       print(f"{skill.name}: {skill.description}")
   ```

4. **🔄 Ativando Skills em Mensagens**
   - **O que e:** Como incluir skills em chamadas de API
   - **Por que aprender:** Uso de skills em aplicacoes
   - **Conceitos-chave:**

   ```python
   response = client.messages.create(
       model="claude-opus-4-5-20251101",
       max_tokens=4096,
       skills=["sales-analyzer", "report-generator"],
       messages=[{"role": "user", "content": "Analyze this sales data"}]
   )
   ```

5. **🏢 Skills em Producao**
   - **O que e:** Consideracoes para uso enterprise
   - **Por que aprender:** Escalar uso de skills
   - **Conceitos-chave:** Rate limits, caching, error handling

6. **📊 Monitoramento e Logs**
   - **O que e:** Observabilidade de skills em producao
   - **Por que aprender:** Debugging e otimizacao
   - **Conceitos-chave:** Logs, metricas, alertas

### Recursos:
- [Agent Skills API Quickstart](https://docs.claude.com/en/api/skills-guide)
- [Claude API Docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

---

## Modulo 2.6 - Brand Identity Skill (Caso de Estudo)

**Duracao:** ~45 min | **Nivel:** Intermediario

### Topicos:

1. **🎨 Conceito da Skill**
   - **O que e:** Skill que mantem consistencia de marca em todo codigo gerado
   - **Por que aprender:** Caso de estudo completo e replicavel
   - **Conceitos-chave:** Design tokens, tech stack, voice/tone

2. **📁 Estrutura de Arquivos**
   - **O que e:** Organizacao da skill brand-identity
   - **Por que aprender:** Padrao para skills multi-arquivo
   - **Conceitos-chave:**

   ```
   brand-identity/
   ├── SKILL.md                    # Router principal
   └── resources/
       ├── design-tokens.json      # Cores, fontes, espacamentos
       ├── tech-stack.md           # React, Tailwind, shadcn/ui
       └── voice-tone.md           # Tom de voz da marca
   ```

3. **📄 SKILL.md como Router**
   - **O que e:** Arquivo principal que direciona para recursos especificos
   - **Por que aprender:** Padrao de navegacao para skills complexas
   - **Conceitos-chave:**

   ```yaml
   ---
   name: brand-identity
   description: Provides single source of truth for brand guidelines, design tokens, technology choices, and voice/tone. Use when generating UI components, styling, writing copy, or creating user-facing assets.
   ---

   # Brand Identity & Guidelines

   ## For Visual Design & UI Styling
   Read: [`resources/design-tokens.json`](resources/design-tokens.json)

   ## For Coding & Component Implementation
   Read: [`resources/tech-stack.md`](resources/tech-stack.md)

   ## For Copywriting & Content Generation
   Read: [`resources/voice-tone.md`](resources/voice-tone.md)
   ```

4. **🎨 design-tokens.json**
   - **O que e:** JSON com valores exatos de cores, fontes, espacamentos
   - **Por que aprender:** Agentes preferem JSON para valores precisos
   - **Conceitos-chave:**

   ```json
   {
     "colors": {
       "primary": { "DEFAULT": "#FACC15", "hover": "#EAB308" },
       "secondary": { "DEFAULT": "#1E40AF" },
       "background": "#111827",
       "destructive": "#EF4444",
       "success": "#10B981"
     },
     "typography": {
       "font_family_headings": ["Inter", "sans-serif"],
       "font_family_body": ["Inter", "sans-serif"]
     }
   }
   ```

5. **⚙️ tech-stack.md**
   - **O que e:** Regras tecnicas estritas (frameworks, padroes)
   - **Por que aprender:** Evita que agente use tecnologias erradas
   - **Conceitos-chave:**

   ```markdown
   # Tech Stack Rules

   ## Core Stack
   - Framework: React (TypeScript)
   - Styling: Tailwind CSS (MANDATORY)
   - Components: shadcn/ui
   - Icons: Lucide React

   ## Forbidden Patterns
   - Do NOT use jQuery
   - Do NOT use Bootstrap
   - Do NOT create CSS files
   ```

6. **✍️ voice-tone.md**
   - **O que e:** Guia de tom de voz para copy gerada
   - **Por que aprender:** Consistencia em textos da marca
   - **Conceitos-chave:**

   ```markdown
   # Voice & Tone Guidelines

   ## Personality
   - Professional but approachable
   - Direct and efficient
   - Tech-savvy but jargon-free

   ## Rules
   - Use Title Case for H1, H2
   - Avoid exclamation points
   - Prefer active voice
   ```

### Recursos:
- [doc/go/2. Brand Design Skill.pdf](doc/go/2.%20Brand%20Design%20Skill%20(1).pdf)

---

## Modulo 2.7 - Integracao com MCP

**Duracao:** ~40 min | **Nivel:** Avancado

### Topicos:

1. **🔗 O que e MCP (Model Context Protocol)**
   - **O que e:** Protocolo para conectar Claude a ferramentas externas
   - **Por que aprender:** MCP + Skills = poder maximo
   - **Conceitos-chave:** Tools, data sources, integrations

2. **⚖️ Skills vs MCP: Quando Usar**
   - **O que e:** Distincao entre conhecimento (Skills) e acoes (MCP)
   - **Por que aprender:** Escolher a abordagem certa
   - **Conceitos-chave:**
     - **MCP:** Conecta a dados (APIs, DBs, arquivos)
     - **Skills:** Define O QUE FAZER com os dados

3. **🔄 Workflow Combinado**
   - **O que e:** Skills que usam dados de MCP servers
   - **Por que aprender:** Automacao end-to-end
   - **Conceitos-chave:**
     1. MCP conecta ao GitHub
     2. Skill define como fazer code review
     3. Resultado: Review automatizado

4. **📊 Exemplo: Analytics Pipeline**
   - **O que e:** MCP para dados + Skill para analise
   - **Por que aprender:** Padrao replicavel
   - **Conceitos-chave:**

   ```
   MCP Server: postgres-mcp (conecta ao banco)
   Skill: customer-health-analyzer (define logica de scoring)

   User: "Analyze customer health for accounts with MRR > 10k"
   1. MCP busca dados do Postgres
   2. Skill aplica algoritmo de health scoring
   3. Output: Relatorio formatado
   ```

5. **🛠️ Configurando MCP + Skills**
   - **O que e:** Setup pratico da integracao
   - **Por que aprender:** Implementacao hands-on
   - **Conceitos-chave:** claude_desktop_config.json, servers, skills

6. **💡 Casos de Uso Avancados**
   - **O que e:** Cenarios complexos de integracao
   - **Por que aprender:** Inspiracao para projetos
   - **Conceitos-chave:**
     - Notion MCP + Meeting Notes Skill
     - GitHub MCP + Code Review Skill
     - Slack MCP + Status Report Skill

### Recursos:
- [Connect Claude Code to tools via MCP](https://code.claude.com/docs/en/mcp)
- [Skills vs MCP Comparison](https://intuitionlabs.ai/articles/claude-skills-vs-mcp)

---

## Modulo 2.8 - Repositorios Comunitarios Claude

**Duracao:** ~35 min | **Nivel:** Todos

### Topicos:

1. **🌟 travisvn/awesome-claude-skills**
   - **O que e:** Lista curada de skills e recursos
   - **Por que aprender:** Descobrir skills prontas
   - **Conceitos-chave:** Curated list, community picks

2. **💼 ComposioHQ/awesome-claude-skills**
   - **O que e:** Skills praticas para produtividade
   - **Por que aprender:** Foco em aplicacoes reais
   - **Conceitos-chave:** Productivity, automation

3. **🧠 alirezarezvani/claude-skills**
   - **O que e:** 48 Domain Expert Skills
   - **Por que aprender:** Skills especializadas por dominio
   - **Conceitos-chave:** Marketing, Engineering, Legal, etc.

4. **🏭 claude-code-skill-factory**
   - **O que e:** Toolkit para criar e deployar skills
   - **Por que aprender:** Acelerar desenvolvimento
   - **Conceitos-chave:** Templates, automation, deployment

5. **🛒 SkillsMP.com (Marketplace)**
   - **O que e:** Marketplace de skills para agentes
   - **Por que aprender:** Descobrir e publicar skills
   - **Conceitos-chave:** Discovery, ratings, downloads

6. **📚 Recursos Educacionais**
   - **O que e:** Tutoriais, videos, artigos
   - **Por que aprender:** Aprendizado continuo
   - **Conceitos-chave:**
     - [egghead.io - Create Your First Skill](https://egghead.io/create-your-first-claude-code-skill~sds93)
     - [Medium - Build Your First Skill](https://medium.com/@richardhightower/build-your-first-claude-code-skill)

### Recursos Completos:
- [GitHub - travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills)
- [GitHub - ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)
- [GitHub - alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)

---

# TRILHA 3: ANTIGRAVITY & GEMINI (Purple)

> **Skills para Gemini CLI e ecossistema Google**

## Modulo 3.1 - Introducao ao AntiGravity

**Duracao:** ~40 min | **Nivel:** Iniciante

### Topicos:

1. **🚀 O que e AntiGravity**
   - **O que e:** Ambiente de agentes de codificacao do Google
   - **Por que aprender:** Alternativa poderosa ao Claude Code
   - **Conceitos-chave:** Gemini-powered, agentic development

2. **📁 Estrutura de Skills AntiGravity**
   - **O que e:** Diretorio `.agent/skills/` (diferente do Claude)
   - **Por que aprender:** Compatibilidade cross-platform
   - **Conceitos-chave:**

   ```
   .agent/skills/skill-name/
   ├── SKILL.md
   ├── scripts/
   ├── examples/
   └── resources/
   ```

3. **🏷️ Diferencas no Frontmatter**
   - **O que e:** Regras especificas do AntiGravity
   - **Por que aprender:** Evitar erros de formatacao
   - **Conceitos-chave:**
     - name: gerundio (testing-code, managing-databases)
     - description: terceira pessoa
     - Max 64 chars nome, 1024 chars description

4. **✍️ Principios de Escrita**
   - **O que e:** The "Claude Way" adaptado para Gemini
   - **Por que aprender:** Instrucoes eficazes
   - **Conceitos-chave:**
     - Conciseness
     - Progressive Disclosure (< 500 linhas)
     - Forward Slashes (sempre `/`, nunca `\`)

5. **🎚️ Graus de Liberdade**
   - **O que e:** Bullet points vs code blocks vs comandos
   - **Por que aprender:** Controle do comportamento
   - **Conceitos-chave:**
     - Bullets = alta liberdade
     - Code blocks = media
     - Bash commands = baixa

6. **📋 Workflow & Feedback Loops**
   - **O que e:** Checklists, validacao, error handling
   - **Por que aprender:** Skills robustas e confiaveis
   - **Conceitos-chave:** Plan-Validate-Execute pattern

### Recursos:
- [doc/go/1. AntiGravity Skills Creator.pdf](doc/go/1.%20AntiGravity%20Skills%20Creator%20(2).pdf)

---

## Modulo 3.2 - B.L.A.S.T. Protocol

**Duracao:** ~45 min | **Nivel:** Intermediario

### Topicos:

1. **🚀 O que e B.L.A.S.T.**
   - **O que e:** Metodologia de desenvolvimento para AntiGravity
   - **Por que aprender:** Framework comprovado para automacao
   - **Conceitos-chave:** Blueprint, Link, Architect, Stylize, Trigger

2. **📋 Phase 1: Blueprint (Vision & Logic)**
   - **O que e:** Definir visao e logica antes de codar
   - **Por que aprender:** Evita retrabalho
   - **Conceitos-chave:**
     - Discovery Questions (5 perguntas)
     - Data-First Rule (schema JSON primeiro)
     - gemini.md como Source of Truth

3. **⚡ Phase 2: Link (Connectivity)**
   - **O que e:** Verificar conexoes e APIs
   - **Por que aprender:** Garantir que integrações funcionam
   - **Conceitos-chave:** API testing, .env validation, handshake scripts

4. **⚙️ Phase 3: Architect (3-Layer Build)**
   - **O que e:** Arquitetura em 3 camadas
   - **Por que aprender:** Separacao de concerns
   - **Conceitos-chave:**
     - Layer 1: Architecture (SOPs em Markdown)
     - Layer 2: Navigation (decision making)
     - Layer 3: Tools (scripts Python determinísticos)

5. **✨ Phase 4: Stylize (Refinement)**
   - **O que e:** Formatacao de outputs e UI
   - **Por que aprender:** Entrega profissional
   - **Conceitos-chave:** Slack blocks, Notion layouts, HTML

6. **🛰️ Phase 5: Trigger (Deployment)**
   - **O que e:** Deploy e automacao
   - **Por que aprender:** Levar para producao
   - **Conceitos-chave:** Cloud transfer, cron jobs, webhooks

### Recursos:
- [doc/go/anti_gravity_blast_master_prompt_en.md](doc/go/anti_gravity_blast_master_prompt_en%20(2).md)

---

## Modulo 3.3 - Google Stitch Skills

**Duracao:** ~40 min | **Nivel:** Intermediario

### Topicos:

1. **🧵 O que e Stitch**
   - **O que e:** Sistema de geracao de UI do Google Labs
   - **Por que aprender:** Skills especializadas para design/frontend
   - **Conceitos-chave:** UI generation, design systems

2. **📦 Repositorio google-labs-code/stitch-skills**
   - **O que e:** Biblioteca oficial de skills Stitch
   - **Por que aprender:** Skills prontas para design
   - **Conceitos-chave:** 1.1k stars, TypeScript

3. **📋 Skills Disponiveis**
   - **O que e:** Skills incluidas no repositorio
   - **Por que aprender:** Saber o que usar
   - **Conceitos-chave:**
     - **design-md:** Gera DESIGN.md para sistemas de design
     - **react-components:** Converte para React
     - **stitch-loop:** Websites multi-pagina de um prompt
     - **enhance-prompt:** Melhora prompts de UI
     - **remotion:** Videos de demonstracao
     - **shadcn-ui:** Integracao com shadcn

4. **🔧 Instalacao via CLI**
   - **O que e:** Comando `npx skills` para instalar
   - **Por que aprender:** Setup rapido
   - **Conceitos-chave:**

   ```bash
   npx skills add google-labs-code/stitch-skills --skill design-md --global
   ```

5. **📁 Estrutura Padronizada**
   - **O que e:** Formato esperado de skills Stitch
   - **Por que aprender:** Criar skills compativeis
   - **Conceitos-chave:**
     - SKILL.md (controle de missao)
     - scripts/ (validacao e rede)
     - resources/ (checklists, style guides)
     - examples/ (golden examples)

6. **💡 Criando Skills para Stitch**
   - **O que e:** Guidelines para novas skills
   - **Por que aprender:** Contribuir ou customizar
   - **Conceitos-chave:** Validation, data decoupling, design generation

### Recursos:
- [GitHub - google-labs-code/stitch-skills](https://github.com/google-labs-code/stitch-skills)

---

## Modulo 3.4 - Gemini CLI Skills

**Duracao:** ~35 min | **Nivel:** Intermediario

### Topicos:

1. **💎 O que e Gemini CLI**
   - **O que e:** CLI do Google para desenvolvimento com Gemini
   - **Por que aprender:** Alternativa ao Claude Code
   - **Conceitos-chave:** Terminal-based, agentic coding

2. **📁 Localizacao de Skills**
   - **O que e:** Onde colocar skills para Gemini CLI
   - **Por que aprender:** Configuracao correta
   - **Conceitos-chave:** .agent/skills/, deteccao automatica

3. **🔄 Compatibilidade com Claude Skills**
   - **O que e:** Skills portaveis entre plataformas
   - **Por que aprender:** Reutilizar trabalho
   - **Conceitos-chave:** Formato AgentSkills.io

4. **⚙️ Configuracao**
   - **O que e:** Setup do ambiente Gemini CLI
   - **Por que aprender:** Comecar a usar
   - **Conceitos-chave:** API keys, project setup

5. **🎯 Skills Recomendadas**
   - **O que e:** Skills que funcionam bem com Gemini
   - **Por que aprender:** Produtividade imediata
   - **Conceitos-chave:** Stitch skills, brand identity

6. **📊 Comparacao Claude vs Gemini**
   - **O que e:** Diferencas na implementacao de skills
   - **Por que aprender:** Escolher a plataforma certa
   - **Conceitos-chave:**

   | Aspecto | Claude Code | Gemini CLI |
   |---------|-------------|------------|
   | Diretorio | .claude/skills/ | .agent/skills/ |
   | Marketplace | /plugin | npx skills |
   | Foco | General purpose | UI/Design forte |

---

## Modulo 3.5 - AntiGravity Skills Creator

**Duracao:** ~40 min | **Nivel:** Avancado

### Topicos:

1. **🏭 Meta-Skill para AntiGravity**
   - **O que e:** System prompt que gera skills automaticamente
   - **Por que aprender:** Acelerar criacao de skills
   - **Conceitos-chave:** antigravity-skill-creator.md

2. **📋 Core Structural Requirements**
   - **O que e:** Regras estruturais obrigatorias
   - **Por que aprender:** Skills validas desde o inicio
   - **Conceitos-chave:**

   ```
   <skill-name>/
   ├── SKILL.md          # Required
   ├── scripts/          # Optional
   ├── examples/         # Optional
   └── resources/        # Optional
   ```

3. **🏷️ YAML Frontmatter Standards**
   - **O que e:** Regras estritas de nomenclatura
   - **Por que aprender:** Evitar erros comuns
   - **Conceitos-chave:**
     - name: gerundio (testing-code)
     - Max 64 chars, lowercase + hyphens
     - Sem "claude" ou "anthropic"

4. **📝 Output Template**
   - **O que e:** Formato de saida do generator
   - **Por que aprender:** Consistencia
   - **Conceitos-chave:**

   ```markdown
   ### [Folder Name]
   **Path:** `.agent/skills/[skill-name]/`

   ### [SKILL.md]
   ---
   name: [gerund-name]
   description: [3rd-person description]
   ---

   # [Skill Title]
   ## When to use this skill
   ## Workflow
   ## Instructions
   ## Resources
   ```

5. **🔄 Workflow & Feedback Loops**
   - **O que e:** Checklists e validacao para tarefas complexas
   - **Por que aprender:** Skills robustas
   - **Conceitos-chave:**
     - Markdown checklists
     - Plan-Validate-Execute pattern
     - Black box error handling

6. **💡 Exemplos de Invocacao**
   - **O que e:** Como usar o creator
   - **Por que aprender:** Aplicacao pratica
   - **Conceitos-chave:**

   ```
   "Based on my skill creator instructions, build me a skill for automating React component testing with Vitest"
   ```

---

## Modulo 3.6 - gemini.md (Project Map)

**Duracao:** ~35 min | **Nivel:** Intermediario

### Topicos:

1. **📍 O que e gemini.md**
   - **O que e:** Arquivo central de estado do projeto (Source of Truth)
   - **Por que aprender:** Manter contexto entre sessoes
   - **Conceitos-chave:** Project map, state tracking

2. **📋 Conteudo do gemini.md**
   - **O que e:** O que documentar no arquivo
   - **Por que aprender:** Organizacao eficaz
   - **Conceitos-chave:**
     - Project state
     - Data schemas
     - Behavioral rules
     - Maintenance log

3. **🔄 Data-First Rule**
   - **O que e:** Definir schema JSON antes de codar
   - **Por que aprender:** Evita retrabalho
   - **Conceitos-chave:**
     - Input shape
     - Output shape
     - Payload confirmation

4. **📁 File Structure Reference**
   - **O que e:** Organizacao do projeto AntiGravity
   - **Por que aprender:** Padrao consistente
   - **Conceitos-chave:**

   ```
   project/
   ├── gemini.md         # Source of Truth
   ├── .env              # Secrets
   ├── architecture/     # SOPs in Markdown
   ├── tools/            # Python scripts
   └── .tmp/             # Intermediate files
   ```

5. **🔧 Self-Annealing (Repair Loop)**
   - **O que e:** Processo de correcao automatica
   - **Por que aprender:** Skills que se auto-corrigem
   - **Conceitos-chave:**
     1. Analyze (read error)
     2. Patch (fix script)
     3. Test (verify)
     4. Update Architecture (prevent repeat)

6. **💡 Exemplo Pratico**
   - **O que e:** gemini.md de um projeto real
   - **Por que aprender:** Template replicavel
   - **Conceitos-chave:** Project context, schemas, rules

---

## Modulo 3.7 - Cross-Platform Compatibility

**Duracao:** ~30 min | **Nivel:** Avancado

### Topicos:

1. **🌐 Formato Universal AgentSkills.io**
   - **O que e:** Especificacao aberta para skills
   - **Por que aprender:** Skills portaveis
   - **Conceitos-chave:** Open standard, multi-platform

2. **📊 Plataformas Suportadas**
   - **O que e:** Agentes compativeis com o formato
   - **Por que aprender:** Saber onde usar skills
   - **Conceitos-chave:**
     - Claude Code, Claude.ai
     - Gemini CLI, AntiGravity
     - Cursor, VS Code
     - GitHub Copilot
     - Roo Code, Goose
     - E muitos outros...

3. **🔄 Adaptando Skills**
   - **O que e:** Ajustes para diferentes plataformas
   - **Por que aprender:** Maximizar reutilizacao
   - **Conceitos-chave:** Diretorio, frontmatter, allowed-tools

4. **📋 Mapeamento de Diretorios**
   - **O que e:** Onde cada plataforma espera skills
   - **Por que aprender:** Instalacao correta
   - **Conceitos-chave:**

   | Plataforma | Diretorio Global | Diretorio Projeto |
   |------------|------------------|-------------------|
   | Claude | ~/.claude/skills/ | .claude/skills/ |
   | AntiGravity | ~/.agent/skills/ | .agent/skills/ |
   | Cursor | ~/.cursor/skills/ | .cursor/skills/ |

5. **🧪 Testando Compatibilidade**
   - **O que e:** Verificar que skill funciona em multiplas plataformas
   - **Por que aprender:** Qualidade cross-platform
   - **Conceitos-chave:** Test matrix, edge cases

6. **💡 Skill Universal de Exemplo**
   - **O que e:** Skill que funciona em todas as plataformas
   - **Por que aprender:** Template replicavel
   - **Conceitos-chave:** Minimal dependencies, standard format

---

## Modulo 3.8 - Casos de Estudo Google

**Duracao:** ~35 min | **Nivel:** Todos

### Topicos:

1. **🎨 design-md Skill**
   - **O que e:** Gera DESIGN.md para sistemas de design
   - **Por que aprender:** Documentacao automatica
   - **Conceitos-chave:** Design systems, UI specs

2. **⚛️ react-components Skill**
   - **O que e:** Converte designs para componentes React
   - **Por que aprender:** Design-to-code automatizado
   - **Conceitos-chave:** TypeScript, validation

3. **🔄 stitch-loop Skill**
   - **O que e:** Cria websites multi-pagina de um prompt
   - **Por que aprender:** Prototipagem rapida
   - **Conceitos-chave:** End-to-end generation

4. **✨ enhance-prompt Skill**
   - **O que e:** Melhora prompts vagos de UI
   - **Por que aprender:** Inputs melhores = outputs melhores
   - **Conceitos-chave:** Prompt optimization

5. **🎬 remotion Skill**
   - **O que e:** Cria videos de demo com Remotion
   - **Por que aprender:** Marketing automatizado
   - **Conceitos-chave:** Video generation, transitions

6. **🧩 shadcn-ui Skill**
   - **O que e:** Integracao com biblioteca shadcn/ui
   - **Por que aprender:** Componentes prontos
   - **Conceitos-chave:** Component library, Tailwind

---

# TRILHA 4: ECOSSISTEMA (Amber)

> **Superpowers, comunidade e marketplaces**

## Modulo 4.1 - Superpowers Framework

**Duracao:** ~45 min | **Nivel:** Intermediario

### Topicos:

1. **🦸 O que e Superpowers**
   - **O que e:** Framework agentic de desenvolvimento de software
   - **Por que aprender:** Metodologia comprovada para coding agents
   - **Conceitos-chave:** obra/superpowers, battle-tested skills

2. **🔄 Workflow de 6 Etapas**
   - **O que e:** Ciclo completo de desenvolvimento
   - **Por que aprender:** Processo estruturado
   - **Conceitos-chave:**
     1. **Brainstorming** - Refinamento interativo do design
     2. **Planning** - Planos com tarefas de 2-5 minutos
     3. **Execution** - Desenvolvimento com subagentes
     4. **TDD** - RED-GREEN-REFACTOR
     5. **Review** - Checklist contra o plano
     6. **Finalization** - Merge, PR ou descarte

3. **📁 Estrutura do Repositorio**
   - **O que e:** Organizacao do projeto superpowers
   - **Por que aprender:** Entender o framework
   - **Conceitos-chave:**

   ```
   superpowers/
   ├── .claude-plugin/    # Config Claude Code
   ├── .codex/            # Setup Codex
   ├── .opencode/         # Setup OpenCode
   ├── agents/            # Implementacoes
   ├── commands/          # Comandos
   ├── skills/            # Biblioteca de skills
   ├── lib/               # Utilitarios
   ├── hooks/             # Integrações
   └── docs/              # Documentação
   ```

4. **🧪 Skills de Testing & Debugging**
   - **O que e:** TDD, Systematic Debugging, Verification
   - **Por que aprender:** Qualidade de codigo
   - **Conceitos-chave:**
     - Test-Driven Development (RED-GREEN-REFACTOR)
     - Systematic Debugging (4 fases)
     - Verification Before Completion

5. **🤝 Skills de Colaboracao**
   - **O que e:** Brainstorming, Plans, Code Review
   - **Por que aprender:** Trabalho em equipe
   - **Conceitos-chave:**
     - Brainstorming (refinamento socratico)
     - Writing Plans (detalhados)
     - Code Review (feedback)
     - Git Worktrees (paralelo)

6. **🔧 Instalacao**
   - **O que e:** Como instalar superpowers
   - **Por que aprender:** Comecar a usar
   - **Conceitos-chave:**

   ```bash
   # Claude Code
   /plugin marketplace add obra/superpowers-marketplace
   /plugin install superpowers@superpowers-marketplace

   # Verificar
   /help
   ```

### Recursos:
- [GitHub - obra/superpowers](https://github.com/obra/superpowers)

---

## Modulo 4.2 - Skills de Desenvolvimento

**Duracao:** ~40 min | **Nivel:** Intermediario

### Topicos:

1. **🧪 test-driven-development Skill**
   - **O que e:** Ciclo RED-GREEN-REFACTOR automatizado
   - **Por que aprender:** TDD sistematico
   - **Conceitos-chave:**

   ```markdown
   ## TDD Cycle
   1. RED: Write failing test
   2. GREEN: Minimal code to pass
   3. REFACTOR: Improve without breaking
   ```

2. **🐛 systematic-debugging Skill**
   - **O que e:** Processo de 4 fases para debugging
   - **Por que aprender:** Debug metodico
   - **Conceitos-chave:**
     1. Reproduce
     2. Isolate
     3. Fix
     4. Verify

3. **📝 code-review Skill**
   - **O que e:** Solicitar e receber feedback de codigo
   - **Por que aprender:** Qualidade e aprendizado
   - **Conceitos-chave:** Checklist, conventions, suggestions

4. **⚠️ error-handling-patterns Skill**
   - **O que e:** Padroes de tratamento de erros
   - **Por que aprender:** Codigo resiliente
   - **Conceitos-chave:**

   ```markdown
   ## Error Categories
   - Recoverable: Network timeouts, validation failures
   - Unrecoverable: Memory exhaustion, stack overflow

   ## Patterns
   - Exceptions vs Result types
   - Circuit Breaker
   - Graceful Degradation
   ```

5. **📋 verification-before-completion Skill**
   - **O que e:** Verificar antes de declarar sucesso
   - **Por que aprender:** Evitar erros silenciosos
   - **Conceitos-chave:** Assertions, smoke tests

6. **🌳 git-worktrees Skill**
   - **O que e:** Desenvolvimento paralelo com worktrees
   - **Por que aprender:** Multiplas features simultaneas
   - **Conceitos-chave:** Branches isolados, contexto limpo

### Recursos:
- [GitHub - wshobson/agents error-handling-patterns](https://github.com/wshobson/agents/blob/main/plugins/developer-essentials/skills/error-handling-patterns/SKILL.md)

---

## Modulo 4.3 - Marketplaces de Skills

**Duracao:** ~35 min | **Nivel:** Todos

### Topicos:

1. **🛒 SkillsMP.com**
   - **O que e:** Marketplace centralizado de skills
   - **Por que aprender:** Descobrir skills prontas
   - **Conceitos-chave:** Discovery, ratings, downloads

2. **📚 SkillsDirectory.com**
   - **O que e:** Diretorio e documentacao de skills
   - **Por que aprender:** Referencia e aprendizado
   - **Conceitos-chave:** SKILL.md format, resources

3. **🌐 AgentSkills.io**
   - **O que e:** Hub oficial do formato AgentSkills
   - **Por que aprender:** Especificacao e exemplos
   - **Conceitos-chave:** Specification, integrations

4. **🏆 AgentSkills.best**
   - **O que e:** Curadoria das melhores skills
   - **Por que aprender:** Quality-assured skills
   - **Conceitos-chave:** Best practices, rated skills

5. **📦 Plugin Marketplaces (por plataforma)**
   - **O que e:** Marketplaces nativos de cada agente
   - **Por que aprender:** Instalacao facil
   - **Conceitos-chave:**
     - Claude: /plugin marketplace
     - AntiGravity: npx skills
     - Cursor: Extension marketplace

6. **💡 Como Publicar Skills**
   - **O que e:** Processo para compartilhar skills
   - **Por que aprender:** Contribuir para comunidade
   - **Conceitos-chave:** GitHub, documentation, testing

---

## Modulo 4.4 - Listas Awesome

**Duracao:** ~30 min | **Nivel:** Todos

### Topicos:

1. **⭐ awesome-claude-skills (travisvn)**
   - **O que e:** Lista curada principal
   - **Por que aprender:** Ponto de entrada para descoberta
   - **Conceitos-chave:** Curated, community picks

2. **⭐ awesome-claude-skills (ComposioHQ)**
   - **O que e:** Foco em produtividade
   - **Por que aprender:** Skills praticas
   - **Conceitos-chave:** Automation, productivity

3. **⭐ awesome-agent-skills (heilcheng)**
   - **O que e:** Lista multi-plataforma
   - **Por que aprender:** Skills para varios agentes
   - **Conceitos-chave:** Claude, Codex, Copilot, VS Code

4. **📋 Como Navegar Listas Awesome**
   - **O que e:** Tecnicas para encontrar skills relevantes
   - **Por que aprender:** Eficiencia na busca
   - **Conceitos-chave:** Categories, stars, activity

5. **🔄 Contribuindo para Listas**
   - **O que e:** Como adicionar skills a listas
   - **Por que aprender:** Compartilhar descobertas
   - **Conceitos-chave:** Pull requests, guidelines

6. **📊 Avaliando Qualidade**
   - **O que e:** Criterios para escolher skills
   - **Por que aprender:** Evitar skills ruins
   - **Conceitos-chave:** Stars, commits, issues, docs

### Recursos:
- [GitHub - travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills)
- [GitHub - heilcheng/awesome-agent-skills](https://github.com/heilcheng/awesome-agent-skills)

---

## Modulo 4.5 - Domain Expert Skills

**Duracao:** ~40 min | **Nivel:** Todos

### Topicos:

1. **📊 Marketing Skills**
   - **O que e:** Skills para analise de marketing
   - **Por que aprender:** Automacao de campanhas
   - **Conceitos-chave:** Analytics, campaigns, content

2. **💰 Finance Skills**
   - **O que e:** Analise financeira automatizada
   - **Por que aprender:** Reports, forecasting
   - **Conceitos-chave:** Revenue analysis, budgeting

3. **⚖️ Legal Skills**
   - **O que e:** Revisao e analise juridica
   - **Por que aprender:** Contratos, compliance
   - **Conceitos-chave:** Contract review, risk analysis

4. **🏥 Healthcare Skills**
   - **O que e:** Analise de dados de saude
   - **Por que aprender:** Insights clinicos
   - **Conceitos-chave:** Patient data, protocols

5. **🛠️ Engineering Skills**
   - **O que e:** Desenvolvimento e DevOps
   - **Por que aprender:** Automacao tecnica
   - **Conceitos-chave:** CI/CD, testing, deployment

6. **📈 Sales & CRM Skills**
   - **O que e:** Analise de vendas e clientes
   - **Por que aprender:** Pipeline, forecasting
   - **Conceitos-chave:** Customer health, churn prediction

### Recursos:
- [GitHub - alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) (48 Domain Expert Skills)

---

## Modulo 4.6 - Criando Skills do Zero

**Duracao:** ~50 min | **Nivel:** Avancado

### Topicos:

1. **🎯 Identificando Necessidades**
   - **O que e:** Como descobrir que skill criar
   - **Por que aprender:** Resolver problemas reais
   - **Conceitos-chave:** Pain points, repeticao, automacao

2. **📝 Design da Skill**
   - **O que e:** Planejar antes de implementar
   - **Por que aprender:** Evitar retrabalho
   - **Conceitos-chave:**
     - Qual problema resolve?
     - Quais triggers ativam?
     - Que outputs produz?
     - Que recursos precisa?

3. **✍️ Escrevendo o SKILL.md**
   - **O que e:** Implementacao passo a passo
   - **Por que aprender:** Hands-on
   - **Conceitos-chave:**

   ```yaml
   ---
   name: my-custom-skill
   description: [O que faz] + [Quando usar] + [Keywords]
   allowed-tools: [Tools necessarias]
   ---

   # [Titulo]

   ## When to Use
   - [Trigger 1]
   - [Trigger 2]

   ## Instructions
   [Logica da skill]

   ## Examples
   [Casos de uso]
   ```

4. **🧪 Testando a Skill**
   - **O que e:** Validacao em cenarios reais
   - **Por que aprender:** Garantir qualidade
   - **Conceitos-chave:**
     - Teste de ativacao
     - Teste de execucao
     - Edge cases
     - Erro handling

5. **📦 Empacotando para Distribuicao**
   - **O que e:** Preparar skill para compartilhar
   - **Por que aprender:** Contribuir para comunidade
   - **Conceitos-chave:**
     - SETUP.md
     - demo-prompt.txt
     - Sample data
     - ZIP package

6. **🚀 Publicando**
   - **O que e:** Onde e como publicar
   - **Por que aprender:** Impacto na comunidade
   - **Conceitos-chave:**
     - GitHub repo proprio
     - Pull request para awesome-lists
     - Marketplace submission

---

## Modulo 4.7 - Integracao com IDEs

**Duracao:** ~35 min | **Nivel:** Intermediario

### Topicos:

1. **💻 Cursor + Skills**
   - **O que e:** Usando skills no Cursor IDE
   - **Por que aprender:** IDE popular para AI coding
   - **Conceitos-chave:** .cursor/skills/, extensions

2. **📝 VS Code + Skills**
   - **O que e:** Skills no Visual Studio Code
   - **Por que aprender:** IDE mais usado
   - **Conceitos-chave:** GitHub Copilot, extensions

3. **🌐 Neovim + Skills**
   - **O que e:** Skills em editores terminal-based
   - **Por que aprender:** Power users
   - **Conceitos-chave:** Plugins, integrations

4. **☁️ IDEs Cloud (Gitpod, Codespaces)**
   - **O que e:** Skills em ambientes cloud
   - **Por que aprender:** Dev environments efemeros
   - **Conceitos-chave:** dotfiles, setup scripts

5. **🔧 Configuracao Unificada**
   - **O que e:** Manter skills sincronizadas
   - **Por que aprender:** Consistencia entre ambientes
   - **Conceitos-chave:** dotfiles repo, symlinks

6. **💡 Workflows por IDE**
   - **O que e:** Best practices por ambiente
   - **Por que aprender:** Maximizar produtividade
   - **Conceitos-chave:** Keybindings, commands

---

## Modulo 4.8 - Futuro das Skills

**Duracao:** ~30 min | **Nivel:** Todos

### Topicos:

1. **🔮 Tendencias 2026-2027**
   - **O que e:** Para onde o ecossistema esta indo
   - **Por que aprender:** Antecipar mudancas
   - **Conceitos-chave:** AI agents, automation

2. **🤖 Skills + AI Agents**
   - **O que e:** Como skills evoluem com agentes
   - **Por que aprender:** Estar preparado
   - **Conceitos-chave:** Autonomous agents, multi-agent

3. **🔗 Skills + MCP Evolution**
   - **O que e:** Integracao mais profunda
   - **Por que aprender:** Poder combinado
   - **Conceitos-chave:** Data + Logic

4. **🌐 Padronizacao Universal**
   - **O que e:** AgentSkills.io como padrao
   - **Por que aprender:** Investir no certo
   - **Conceitos-chave:** Open standard, adoption

5. **💼 Skills Enterprise**
   - **O que e:** Uso corporativo de skills
   - **Por que aprender:** Oportunidades de mercado
   - **Conceitos-chave:** Security, governance, scale

6. **🚀 Oportunidades**
   - **O que e:** Como se posicionar no ecossistema
   - **Por que aprender:** Carreira e negocios
   - **Conceitos-chave:**
     - Criador de skills
     - Consultor de automacao
     - Contribuidor open-source

---

# TRILHA 5: SKILLS UNIVERSAL (Cyan)

> **O padrao universal de Agent Skills para todas as plataformas**

## Modulo 5.1 - O Padrao Agent Skills

**Duracao:** ~35 min | **Nivel:** Iniciante

### Topicos:
1. **📋 AgentSkills.io spec** - O que e e quem criou
2. **📄 SKILL.md como formato universal** - Formato padrao entre plataformas
3. **🏷️ YAML frontmatter** - Campos obrigatorios vs opcionais
4. **📖 Progressive disclosure** - Como organizar conteudo gradualmente
5. **✅ Vantagens da padronizacao** - Por que padronizar skills
6. **🌐 Adocao pelas grandes plataformas** - Microsoft, OpenAI, Google, etc.

---

## Modulo 5.2 - Skills no GitHub Copilot

**Duracao:** ~40 min | **Nivel:** Intermediario

### Topicos:
1. **🤖 GitHub Copilot e skills** - Visao geral da integracao
2. **📂 Repo-level skills** - .github/copilot/ e configuracao
3. **🏢 Organization-wide skills** - Skills compartilhadas na org
4. **📋 AGENTS.md** - Formato nativo do Copilot
5. **⚖️ SKILL.md vs AGENTS.md** - Quando usar cada um
6. **✅ Boas praticas para Copilot skills** - Dicas e patterns

---

## Modulo 5.3 - Skills no Cursor

**Duracao:** ~40 min | **Nivel:** Intermediario

### Topicos:
1. **📜 .cursorrules** - O formato legacy do Cursor
2. **📄 .mdc** - O formato moderno do Cursor
3. **📋 SKILL.md no Cursor** - Compatibilidade e uso
4. **🛒 Cursor Directory** - Marketplace de regras
5. **🔄 Migracao .cursorrules → SKILL.md** - Guia passo a passo
6. **💡 Dicas avancadas** - Otimizacao e patterns

---

## Modulo 5.4 - Skills no Manus AI

**Duracao:** ~35 min | **Nivel:** Intermediario

### Topicos:
1. **🖥️ O que e o Manus AI** - Overview da plataforma
2. **💻 VM completa** - Ambiente Ubuntu integrado
3. **🤖 Execucao autonoma de skills** - Como funciona
4. **⚙️ Geracao automatica de skills** - Manus gera skills
5. **⚠️ Limitacoes e consideracoes** - O que saber
6. **💡 Casos de uso praticos** - Exemplos reais

---

## Modulo 5.5 - Skills no Cline & OpenCode

**Duracao:** ~35 min | **Nivel:** Intermediario

### Topicos:
1. **🔌 Cline** - O que e e como funciona
2. **📦 Skills no Cline 3.48+** - Suporte experimental
3. **⚙️ Configuracao e ativacao** - Setup passo a passo
4. **🔧 OpenCode plugins** - Sistema de plugins
5. **📋 Compatibilidade com SKILL.md** - Formato universal
6. **🐛 Troubleshooting** - Problemas comuns e solucoes

---

## Modulo 5.6 - Skills no OpenAI Codex

**Duracao:** ~40 min | **Nivel:** Intermediario

### Topicos:
1. **🧪 OpenAI Codex** - Overview da plataforma
2. **📂 Diretorio .agents/skills/** - Onde colocar skills
3. **📋 AGENTS.md no Codex** - Formato nativo
4. **📦 Catalogo openai/skills** - Repositorio no GitHub
5. **🔄 Compatibilidade cross-platform** - Portabilidade
6. **✍️ Criando skills para Codex** - Guia pratico

---

## Modulo 5.7 - SKILL.md vs AGENTS.md vs .cursorrules

**Duracao:** ~40 min | **Nivel:** Todos

### Topicos:
1. **📊 Tabela comparativa dos formatos** - Side-by-side
2. **📋 SKILL.md** - Pontos fortes e fracos
3. **📄 AGENTS.md** - Pontos fortes e fracos
4. **📜 .cursorrules/.mdc** - Pontos fortes e fracos
5. **🔄 Estrategia de migracao** - Como migrar entre formatos
6. **🔮 Tendencias e futuro** - Para onde vai o mercado

---

## Modulo 5.8 - Portabilidade Cross-Platform

**Duracao:** ~45 min | **Nivel:** Avancado

### Topicos:
1. **🌐 Principio write-once-run-anywhere** - A filosofia
2. **📁 Estrutura de diretorios multi-plataforma** - Organizacao
3. **🧪 Testing de portabilidade** - Verificacao cross-platform
4. **🛒 Marketplaces de skills** - Onde publicar
5. **🔧 agent-skills-cli** - Ferramenta CLI para gerenciamento
6. **🚀 Publicando sua primeira skill universal** - Guia completo

---

# TRILHA 6: EXEMPLOS & APLICACOES (Rose)

> **Repositorios reais, colecoes awesome e ferramentas do ecossistema**

## Modulo 6.1 - Repositorios Oficiais

**Duracao:** ~35 min | **Nivel:** Todos

### Topicos:
1. **🏛️ anthropics/skills** - Repositorio oficial da Anthropic
2. **Ⓜ️ microsoft/skills** - Skills da Microsoft
3. **🤖 openai/skills** - Catalogo do OpenAI Codex
4. **▲ vercel-labs/agent-skills** - Vercel e Next.js
5. **⚡ supabase/agent-skills** - Supabase skills
6. **📱 callstackincubator/agent-skills** - React Native skills

---

## Modulo 6.2 - Colecoes Awesome

**Duracao:** ~30 min | **Nivel:** Todos

### Topicos:
1. **⭐ VoltAgent/awesome-agent-skills** - 300+ skills curadas
2. **🚀 sickn33/antigravity-awesome-skills** - 800+ skills AntiGravity
3. **📋 travisvn/awesome-claude-skills** - Colecao Claude
4. **💼 ComposioHQ/awesome-claude-skills** - Foco produtividade
5. **🤖 skillmatic-ai/awesome-agent-skills** - Multi-plataforma
6. **🤝 Como contribuir** - Adicionando suas skills

---

## Modulo 6.3 - Superpowers Framework

**Duracao:** ~45 min | **Nivel:** Intermediario

### Topicos:
1. **💪 O que e o Superpowers (27K+ stars)** - Overview
2. **🔄 Workflow de 6 passos** - Brainstorm, Plan, Execute, TDD, Review, Finalize
3. **🧪 TDD com Superpowers** - RED-GREEN-REFACTOR
4. **🐛 Debugging e brainstorming** - Skills auxiliares
5. **🔀 Forks e variacoes populares** - Adaptacoes da comunidade
6. **⚙️ Adaptando ao seu workflow** - Customizacao

---

## Modulo 6.4 - Skills de Desenvolvimento

**Duracao:** ~40 min | **Nivel:** Intermediario

### Topicos:
1. **📦 levnikolaevich/claude-code-skills (99 skills)** - Colecao massiva
2. **🏗️ ramziddin/solid-skills** - Principios SOLID
3. **🧪 TDD skills** - Test-driven development
4. **📝 Code review automatizado** - Review por agentes
5. **🐛 Debugging skills avancadas** - Depuracao sistematica
6. **🔧 CI/CD e DevOps skills** - Automacao de pipeline

---

## Modulo 6.5 - Skills de Dominio

**Duracao:** ~35 min | **Nivel:** Intermediario

### Topicos:
1. **🧠 alirezarezvani/claude-skills (53 domain experts)** - Colecao completa
2. **📊 product-on-purpose/pm-skills** - Product Management
3. **🎨 ehmo/platform-design-skills (300+ rules)** - Design de plataforma
4. **📈 Data science skills** - Analise de dados
5. **✍️ Marketing e conteudo skills** - Criacao de conteudo
6. **🔧 Criando skills de dominio customizadas** - Guia pratico

---

## Modulo 6.6 - Multi-Agent & Subagents

**Duracao:** ~40 min | **Nivel:** Avancado

### Topicos:
1. **🤝 VoltAgent/awesome-claude-code-subagents (100+)** - Colecao de subagentes
2. **🤖 wshobson/agents (112 agents)** - Biblioteca completa
3. **🐝 ccswarm** - Coordenacao de agentes
4. **🎼 maestro-gemini** - Orquestracao Google
5. **📡 Padroes de comunicacao multi-agent** - Arquiteturas
6. **🏗️ Construindo seu sistema multi-agent** - Hands-on

---

## Modulo 6.7 - Skills para Cursor & Windsurf

**Duracao:** ~35 min | **Nivel:** Intermediario

### Topicos:
1. **📜 PatrickJS/awesome-cursorrules** - A referencia principal
2. **🏄 Windsurf-Samples/cascade-customizations-catalog** - Catalogo Windsurf
3. **🏄 RuleSurf** - Gerenciador de regras
4. **🧠 cascade-memory-bank** - Memoria persistente
5. **🔄 Migracoes entre Cursor e Windsurf** - Guia pratico
6. **⚡ Criando regras otimizadas** - Best practices

---

## Modulo 6.8 - Marketplaces & Ferramentas

**Duracao:** ~35 min | **Nivel:** Todos

### Topicos:
1. **🛒 SkillsMP.com** - Marketplace de skills
2. **🌐 AgentSkills.io** - Especificacao e diretorio
3. **🔧 agent-skills-cli** - Ferramenta de linha de comando
4. **📦 skillport e n-skills** - Gerenciadores de pacotes
5. **🏭 skill-creator** - Geradores automaticos
6. **🚀 Como publicar sua skill** - Guia completo de publicacao

---

# RECURSOS COMPLEMENTARES

## Links Oficiais

### Documentacao
- [Claude Code Docs - Skills](https://code.claude.com/docs/en/skills)
- [Claude Help Center - Creating Skills](https://support.claude.com/en/articles/12512198-how-to-create-custom-skills)
- [Claude Help Center - Using Skills](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- [AgentSkills.io Specification](https://agentskills.io/specification)

### Repositorios Oficiais
- [GitHub - anthropics/skills](https://github.com/anthropics/skills)
- [GitHub - google-labs-code/stitch-skills](https://github.com/google-labs-code/stitch-skills)
- [GitHub - agentskills/agentskills](https://github.com/agentskills/agentskills)

### Repositorios Comunitarios
- [GitHub - obra/superpowers](https://github.com/obra/superpowers)
- [GitHub - travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills)
- [GitHub - ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)
- [GitHub - alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)
- [GitHub - heilcheng/awesome-agent-skills](https://github.com/heilcheng/awesome-agent-skills)

## Tutoriais em Video

- [YouTube - Claude Skills Tutorial](https://youtu.be/7_SL0FaY8MM)
- [egghead.io - Create Your First Skill](https://egghead.io/create-your-first-claude-code-skill~sds93)

## Artigos Recomendados

- [Simon Willison - Skills are awesome](https://simonwillison.net/2025/Oct/16/claude-skills/)
- [Inside Claude Code Skills - Mikhail Shilkov](https://mikhail.io/2025/10/claude-code-skills/)
- [How to Make Skills Activate Reliably - Scott Spence](https://scottspence.com/posts/how-to-make-claude-code-skills-activate-reliably)
- [Skills vs MCP Comparison](https://intuitionlabs.ai/articles/claude-skills-vs-mcp)

## Marketplaces

- [SkillsMP.com](https://skillsmp.com/)
- [SkillsDirectory.com](https://www.skillsdirectory.com/)
- [AgentSkills.io](https://agentskills.io/home)

---

# TEMPLATES PARA CADA MODULO

## Template de Pagina de Trilha
Usar cores conforme:
- T1 Fundamentos: **Emerald**
- T2 Claude Code: **Blue**
- T3 AntiGravity & Gemini: **Purple**
- T4 Ecossistema: **Amber**
- T5 Skills Universal: **Cyan**
- T6 Exemplos & Aplicacoes: **Rose**

## Template de Pagina de Modulo
- 6 topicos detalhados
- Boxes de conceito, dados, dicas
- Grid fazer/evitar
- Resumo final

---

# PROXIMOS PASSOS

1. **Aprovar estrutura do curso**
2. **Gerar paginas HTML** usando MASTER_COMPLETO.md
3. **Adicionar exemplos praticos** de cada skill
4. **Incluir exercicios hands-on** por modulo
5. **Criar slides** para apresentacoes

---

**Versao:** 2.0
**Ultima atualizacao:** 2026-02-14
