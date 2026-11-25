# Validador de Sitemap XML

[![Validador Sitemap](https://img.shields.io/badge/TAVARDT-Sitemap%20XML-5b3cf5.svg)](https://tools.tavardt.com/pt/verificador-sitemap-xml/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Ferramenta automatizada de verificacao de sitemaps XML em Portugal, assegurando conformidade com o protocolo Sitemaps.org e indexacao sem erros pelos motores de busca.

***

## Capacidades de Validacao de Sitemaps XML

* **Conformidade Estrutural XML**: Validacao de ficheiros `<urlset>` e indices `<sitemapindex>` de acordo com o protocolo sitemaps.org.
* **Formatacao de Atributos**: Rastreio de datas `<lastmod>`, valores de `<priority>` e frequencia de atualizacao `<changefreq>`.
* **Consistencia de Protocolo**: Deteccao de ligações inseguras em HTTP dentro de dominios cifrados e formatacao de URLs.
* **Limites de Capacidade**: Verificacao das quotas oficiais de 50.000 entradas e limites dimensionais.
* **Indice de Qualidade do Sitemap**: Avaliacao rigorosa de 0 a 100 com alertas tecnicos priorizados.

***

## Instalação e Execucao

Requer Python 3.8 ou superior, utilizando unicamente a biblioteca padrao.

```bash
git clone https://github.com/TAVARDT-Portugal/xml-sitemap-validator-pt.git
cd xml-sitemap-validator-pt
python sitemap_validator.py https://exemplo.pt/sitemap.xml
```

Para exportacao em JSON:

```bash
python sitemap_validator.py https://exemplo.pt/sitemap.xml -json
```

***

## Consultoria em Indexacao e SEO Tecnico

Para projetos complexos de rastreio de plataformas de larga escala e conformidade com Normas W3C e Protocolo Sitemaps.org, contacte a **TAVARDT**.

***



## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/pt/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/pt/
* **Contacto Técnico:** https://ag.tavardt.com/pt/contacto/

***

### Licença
Distribuído sob a Licença MIT.

***

© 2026 TAVARDT. All rights reserved.
