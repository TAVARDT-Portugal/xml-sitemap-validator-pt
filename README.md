<p align="center">
  <a href="https://ag.tavardt.com/pt/">
    <img src="https://ag.tavardt.com/img/tavardt-banner.png" alt="TAVARDT" width="1024" />
  </a>
</p>

# Validador de Sitemap XML e Estrutura de Protocolo

[![Validador Sitemap](https://img.shields.io/badge/TAVARDT-Sitemap%20XML-5b3cf5.svg)](https://tools.tavardt.com/pt/verificador-sitemap-xml/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

O **TAVARDT Validador de Sitemap XML** disponibiliza auditoria automatizada de sintaxe, validação de esquemas de protocolo, controlo de volume de URLs e identificação de conteúdo misto para sitemaps em Portugal.

***

## Arquitetura do Protocolo e Matriz Diagnóstica

Os motores de busca utilizam sitemaps XML estruturados para rastrear novos conteúdos e programar a periodicidade de indexação. Erros de sintaxe, ficheiros desmesurados ou hiperligações inseguras desperdiçam o orçamento de rastreio e atrasam a indexação.

Esta ferramenta analisa a integridade do XML, valida esquemas urlset e sitemapindex, fiscaliza o teto de 50.000 URLs e identifica ligações não seguras com base em 100 pontos sem dependências externas.

O motor analítico avalia os ficheiros sitemap de acordo com as especificações Sitemaps.org e requisitos dos motores de pesquisa:

<table>
  <thead>
    <tr>
      <th>Verificação de Protocolo</th><th>Critério de Validação</th><th>Dedução</th><th>Impacto em Rastreio e SEO</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Integridade da Sintaxe XML</strong></td><td>Parsing completo via ElementTree. Deteta caracteres reservados (&amp;) não escapados, fecho incorreto de tags e erros de codificação.</td><td>Pontuação zerada (0 pts)</td><td>Falha crítica; rastreadores de pesquisa rejeitam o ficheiro por completo.</td>
    </tr>
    <tr>
      <td><strong>Validação do Elemento Raiz</strong></td><td>Exige conformidade estrita com o padrão Sitemaps.org: deve ser <code>&lt;urlset&gt;</code> ou <code>&lt;sitemapindex&gt;</code>.</td><td>-40 pts</td><td>Estrutura desconhecida que impede a leitura automatizada dos links.</td>
    </tr>
    <tr>
      <td><strong>Limite de Entradas e Volume</strong></td><td>Fiscaliza o teto de 50.000 itens. Penaliza ficheiros vazios (-30 pts) e ficheiros excessivos (&gt;50.000 URLs, -20 pts).</td><td>Até -30 pts</td><td>Esgotamento de memória do bot ou submissão de ficheiro sem conteúdo útil.</td>
    </tr>
    <tr>
      <td><strong>URLs HTTP em Sitemap HTTPS</strong></td><td>Identifica hiperligações inseguras <code>http://</code> declaradas em sites cuja comunicação oficial decorre sob HTTPS.</td><td>-15 pts</td><td>Desperdício de orçamento de rastreio em redirecionamentos desnecessários.</td>
    </tr>
    <tr>
      <td><strong>Disponibilidade de Rede</strong></td><td>Verifica código de estado HTTP 200 e tempo de resposta durante a negociação TLS.</td><td>Pontuação zerada (0 pts)</td><td>Servidor inacessível impossibilitando a ingestão de metadados de pesquisa.</td>
    </tr>
  </tbody>
</table>

### Escala de Qualidade e Níveis de Estado

O utilitário atribui um índice global de conformidade classificando a integridade do ficheiro XML:

* <strong>85 a 100 (OPTIMAL)</strong>: Conformidade total; sintaxe perfeita, URLs seguras via HTTPS e volume de entradas adequado.
* <strong>65 a 84 (WARNING)</strong>: Ficheiro funcional apresentando pequenos avisos de protocolo misto ou volume elevado.
* <strong>0 a 64 (CRITICAL)</strong>: Falhas estruturais graves, esquemas inválidos ou ficheiro vazio exigindo correção urgente.

***

## Instalação e Execução

Construído exclusivamente com a biblioteca padrão do Python 3.8+, sem qualquer dependência externa.

```bash
git clone https://github.com/TAVARDT-Portugal/xml-sitemap-validator-pt.git
cd xml-sitemap-validator-pt
```

### Execução Padrão via CLI

```bash
python sitemap_validator.py https://exemplo.pt/sitemap.xml
```

### Saída Estruturada para Pipelines em JSON

```bash
python sitemap_validator.py https://exemplo.pt/sitemap.xml -j
```

### Configuração de Timeout Personalizado

```bash
python sitemap_validator.py https://exemplo.pt/sitemap.xml -j -t 15
```

***

## Conformidade e Integridade Digital em Portugal

A manutenção de sitemaps limpos e estruturados responde às recomendações de segurança e integridade de ativos web em Portugal. Eliminar hiperligações inseguras protege os utilizadores e reforça a autoridade institucional.

Recomenda-se a integração de testes automatizados de sitemaps nos processos contínuos de desenvolvimento para garantir uma indexação fiável.

***

## Perguntas Frequentes Técnicas

### Qual é o limite máximo de entradas permitido por ficheiro de sitemap?

O protocolo oficial do Sitemaps.org estipula um limite de 50.000 URLs e 50MB por ficheiro individual descompactado. Ficheiros que ultrapassam 50.000 entradas sofrem dedução de 20 pontos e devem ser fragmentados através de um índice de sitemaps.

### Por que razão as URLs inseguras em HTTP recebem penalidades?

Listar URLs com protocolo HTTP inseguro em sitemaps de sites que operam sob HTTPS causa confusão nos rastreadores, força redirecionamentos desnecessários e degrada sinais de segurança. O validador deduz 15 pontos ao encontrar links HTTP.

### Como a ferramenta diferencia ficheiros urlset de sitemapindex?

O analisador verifica o elemento XML raiz, diferenciando a validação entre <code>&lt;sitemapindex&gt;</code> para sitemaps subordinados e <code>&lt;urlset&gt;</code> para documentos individuais. Estruturas raiz não reconhecidas sofrem perda de 40 pontos.

### O que sucede quando ocorre um erro de sintaxe no ficheiro XML?

Falhas de formatação como caracteres reservados (&amp;) não escapados, tags mal fechadas ou problemas de codificação impedem os motores de pesquisa de ler o documento. O utilitário zera a pontuação e classifica o sitemap como CRITICAL.

### O que significam as faixas de status e pontuação de qualidade?

Notas entre 85 e 100 pontos refletem conformidade OPTIMAL. Entre 65 e 84 pontos o status é WARNING, sinalizando correções recomendadas, e abaixo de 65 pontos o status é CRITICAL, exigindo saneamento estrutural imediato.

***

## Apoio Técnico e Consultoria Especializada

Para auditorias técnicas de SEO, estruturação de sitemaps e integridade aplicacional, consulte os especialistas da **TAVARDT**.

***

## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/pt/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/pt/
* **Contacto Técnico:** https://ag.tavardt.com/pt/contacto/

***

### Licença
Distribuído sob a Licença MIT.

***

© 2026 TAVARDT. Todos os direitos reservados.
