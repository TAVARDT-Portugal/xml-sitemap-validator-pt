# Verificador de Sitemap XML | TAVARDT Portugal

[![Validador Sitemap](https://img.shields.io/badge/TAVARDT-Sitemap%20XML-5b3cf5.svg)](https://tools.tavardt.com/pt/verificador-sitemap-xml/)
[![Jurisdicao](https://img.shields.io/badge/Jurisdicao-Portugal-00C853.svg)](https://ag.tavardt.com/pt/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)

Auditoria tecnica de sitemaps XML e sitemap indexes, validacao de integridade de ligacoes, conformidade sitemaps.org e rastreabilidade.

Desenvolvido e mantido pelo departamento de indexacao tecnica da **[TAVARDT Portugal](https://ag.tavardt.com/pt/)**.

---

## Capacidades de Validacao de Sitemaps XML

* **Conformidade Estrutural XML**: Validacao de ficheiros `<urlset>` e indices `<sitemapindex>` de acordo com o protocolo sitemaps.org.
* **Formatacao de Atributos**: Rastreio de datas `<lastmod>`, valores de `<priority>` e frequencia de atualizacao `<changefreq>`.
* **Consistencia de Protocolo**: Deteccao de ligacoes inseguras em HTTP dentro de dominios cifrados e formatacao de URLs.
* **Limites de Capacidade**: Verificacao das quotas oficiais de 50.000 entradas e limites dimensionais.
* **Indice de Qualidade do Sitemap**: Avaliacao rigorosa de 0 a 100 com alertas tecnicos priorizados.

---

## Instalacao e Execucao

Requer Python 3.8 ou superior, utilizando unicamente a biblioteca padrao.

```bash
git clone https://github.com/TAVARDT-Portugal/xml-sitemap-validator-pt.git
cd xml-sitemap-validator-pt
python sitemap_validator.py https://exemplo.pt/sitemap.xml
```

Para exportacao em JSON:

```bash
python sitemap_validator.py https://exemplo.pt/sitemap.xml --json
```

---

## Plataforma Online de Diagnostico

Para auditorias imediatas de ficheiros XML e gestao de indexacao:

* **[Verificador de Sitemap XML Oficial](https://tools.tavardt.com/pt/verificador-sitemap-xml/)**
* **[Portal Corporativo TAVARDT Portugal](https://ag.tavardt.com/pt/)**

---

## Consultoria em Indexacao e SEO Tecnico

Para projetos complexos de rastreio de plataformas de larga escala e conformidade com Normas W3C e Protocolo Sitemaps.org, contacte a **[TAVARDT Portugal](https://ag.tavardt.com/pt/contato/)**.
