# Sobre Tag Manager

## [Google Analytics Tools](https://ga-dev-tools.appspot.com/#about)

![Tools and demos](images/analytics-tools-cover.png)

Herramientas para realizar pruebas de integración con el API de Google Analytics

- API Query Explorer
- Campaign URL builder
- Documentación para e-commerce
- GA4 Events

## Pruebas auto-tagging AdWords

Se debe verificar que los enlaces finales estén apuntando a las campañas de AdWords contengan el parámetro 'gclid'

- Realizar una prueba agregando el parámetro ?gclid=Test-123
- Examinar que el parámetro gclid este presente en las url y en caso de existir una redirección no se debe de perder.
- Se puede usar la herramienta de [Google Tag Assistant](https://get.google.com/tagassistant/) para grabar las solicitudes al sitio y posteriormente analizar el resultado.

**Referencias:**

- [Sobre el parámetro gclid](https://support.google.com/analytics/answer/1714454#zippy=%2Cuntagged-landing-pages%2Cmanually-tagged-ad-destination-urls-missing-information%2Cthird-party-redirects-drop-campaign-related-url-parameters)
- [Verificar el auto-tagging](https://support.google.com/analytics/answer/2938246?hl=en)

## Cross Domain - etiquetado manual

Para etiquetar de forma manual todos los enlaces del sitio se puede usar el siguiente script.

```javascript
<html>
<body>
  <a href='http://test-domain.net/test-sss/#/site.html?click=true'>Click me</a>
  <a href="https://pruebas.com/#/data/2021-02-07/2021-02-09?r[0].adults=2&r[0].children=0&_ga=2.57691241.2128202229.1611272462-8908134.1608136140">Click me</a>
  <a href='https://book-now.com/#/rooms-available/jueves/3/5?ro=1'>Click me</a>
  <h3>Result</h3>
  <ul id="result"></ul>
  <script>
    (function (i, s, o, g, r, a, m) {
      i['GoogleAnalyticsObject'] = r; i[r] = i[r] || function () {
        (i[r].q = i[r].q || []).push(arguments)
      }, i[r].l = 1 * new Date(); a = s.createElement(o),
        m = s.getElementsByTagName(o)[0]; a.async = 1; a.src = g; m.parentNode.insertBefore(a, m)
    })(window, document, 'script', '//www.google-analytics.com/analytics.js', 'ga');
    ga('create', 'UA-111111111-1', 'auto');
    ga('require', 'displayfeatures');
    // Load the cross-domain linker plugin.
    ga('require', 'linker');
    var result = document.getElementById("result");
    // Iterate all links elements
    var links = document.querySelectorAll("a");
    links.forEach(function(link) {
      link.addEventListener('click', function (event) {
        event.preventDefault();
        event.stopPropagation();
        ga(function (tracker) {
          var linkerParam = tracker.get('linkerParam');
          console.log(link.getAttribute('href'));
          var uri = buildUrl(link.getAttribute('href'), linkerParam)
          console.log(uri);
          link.setAttribute('href',uri);
          var node = document.createElement("li");
          var item = document.createTextNode(link.getAttribute('href'));
          node.appendChild(item);
          result.appendChild(node);
        });
      });
    });

    function buildUrl(baseURL,linkerParam){
      return baseURL.indexOf('?')>-1 ? baseURL + '&' + linkerParam : baseURL + '?' + linkerParam
    }
  </script>
</body>
</html>
```

**Referencias:**

- [Pruebas](https://jsfiddle.net/lgzarturo/2q0fg8mo/)
- [Documentación medición multi-dominio](https://developers.google.com/analytics/devguides/collection/analyticsjs/cross-domain#autolink)
- [Resolver problemas con GA Múltiple dominio](https://www.simoahava.com/analytics/troubleshooting-cross-domain-tracking-in-google-analytics/)
- [Multi-Domain tracking](https://www.optimizesmart.com/cross-domain-tracking-in-google-tag-manager/)
- [Multi-Domain tracking 'Official'][https://support.google.com/analytics/answer/1034342?hl=en]
- [Cross Domain Tracking With Google Tag Manager](https://www.bounteous.com/insights/2015/06/16/cross-domain-tracking-google-tag-manager/)
- [Auto Link Domains: Multidominio en Google Analytics vía GTM](https://aukera.es/blog/auto-link-domains/)
- [Google Analytics Cross Domain Tracking with Google Tag Manager. The Guide](https://www.analyticsmania.com/post/google-analytics-cross-domain-tracking-with-google-tag-manager/)

## Facebook pixel

- [Custom Tag para facebook pixel](https://www.simoahava.com/custom-templates/facebook-pixel/)
