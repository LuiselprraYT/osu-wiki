# Mantenimiento de osu! wiki

*Ver también: [Guía de Contribución de la osu! wiki](/wiki/osu!_wiki/Contribution_guide)*

Este articulo describe aspectos tecnicos y administrativos de la osu! wiki. Tambien cubre los procesos de mantenimiento, los cuales son requeridos para mantenerla al dia, tu puedes ayudar con [uno de ellos](#routines). Para toda discucion relacionada con la wiki, usa el canal `#osu-wiki` en el [servidor de Discord de osu!dev](/wiki/Community/osu!dev_Discord_server).

## Administradores

*Sitio principal: [Lista de administradores de la osu! wiki](/wiki/osu!_wiki/Maintenance/List_of_maintainers)*

Los administradores son personas con [permisos de colaborador](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-user-account/managing-user-account-settings/permission-levels-for-a-user-account-repository#collaborator-access-for-a-repository-owned-by-a-user-account) en el [repositorio `ppy/osu-wiki`](https://github.com/ppy/osu-wiki/), donde todos los articulos y noticias son publicados y almacenados. Ellos pueden clasificar y etiquetar problemas, administrar "pull request" y hacer desiciones con respecto al presente y futuro de la osu!wiki.

Administradores llevan a cabo la ultioma revision de las "pull request" y las unen. Si tu tienes una contribucion que necesita atencion, puedes preguntarle a uno de ellos en el canal `#osu-wiki`.

## Detalles tecnicos

### Rastreador de problemas (Issue tracker)

El [rastreador de problemas](https://github.com/ppy/osu-wiki/issues) contiene ideas y peticiones de posibles mejoras, para los articulosy partes relacionadas al sitio web de la wiki. Abre un problema si tienes una peticion futura, o si haz encontrado un problema en una de las paginas. Por favor ten en cuenta que **esto solo esta limitado a la osu !wiki**, si necesitas ayuda con otros proyectos oficiales relacionados a osu!, usa sus propios rastreadores de problemas:

- [osu!(lazer)](https://github.com/ppy/osu)
- [Sitio web de osu!](https://github.com/ppy/osu-web/)
- [Problemas de osu!(stable)](https://github.com/ppy/osu-stable-issues)

#### Etiquetado de problemas (issue labels)

En GitHub, "pull request" y los problemas pueden ser mencionadas y clasificadas usando [etiquetas (labels)](https://github.com/ppy/osu-wiki/labels), las cuales muestran diferentes aspectos de una "pull request" o un problema. Las etiquetas son informacionales, agregadas por los administradores de la wiki, y por lo general se explican por sí mismo. Mientras estas no requieren alguna accion por parte de la perspectiva del usuario, etiquetas rojas funcionan como recordatorio o para llamar la atencion de otros administradores:

- `rule change` (cambio de regla): el cambio afecta un conjunto de reglas existentes como los [criterios de calificacion](/wiki/Ranking_Criteria), y estos necesitan ser revisados por el encargado del area.
- `blocked` (bloqueado): el cambio tiene problemas que deberan resolverse antes de proceder, o dependiendo de otro problema que debera ser resuelto primero
- `needs native review` (necesita revision nativa): la traduccion necesita ser revisada por una persona con fluidez en el idioma respectivo; alternativamente, durante el proceso de union significa que no se llevo a cabo ninguna revision
- `needs rebase` (necesita reestructuración): la 'pull request' tiene demaciados acometidos pequenos sin esctructura , los cuales deberan ser reestructurados y redactados en una mejor manera; esto usualmente es hecho por los administradores antes de hacer la union

### Enlaces y redirecciones

La mayoria de los articulos de la osu! wiki contienen enlaces alternativos, que son confugurados usando el archivo [`redirect.yaml`](https://github.com/ppy/osu-wiki/blob/master/wiki/redirect.yaml). Las redirecciones están destinadas a ser utilizadas fuera de osu! wiki, por ejemplo, en los foros, o en el [chat](/wiki/Client/Interface/Chat_console), donde 
Most osu! wiki articles have alternative links, which are set up using the [`redirect.yaml`](https://github.com/ppy/osu-wiki/blob/master/wiki/redirect.yaml) file. The redirects are meant to be used outside the osu! wiki, for example, on the forums, or in the [chat](/wiki/Client/Interface/Chat_console), donde se pueden convertir rápidamente en una referencia en línea: 

```
De acuerdo con el [[RC]], esto esta prohibido.
```

Al agregar redirecciones para un artículo nuevo o existente, ten en cuenta que deben ser concisos y diseñados para uso real.

### Integracion continua (CI checks)

El repositorio de la osu! wiki usa la [integracion continua](https://docs.github.com/en/actions/guides/about-continuous-integration) (CI) para revisar de manera automatica las 'pull request' entrantes por varios errores comunes. La lista de revisiones esta configurada al archivo [`continuous-integration.yml`](https://github.com/ppy/osu-wiki/blob/master/.github/workflows/continuous-integration.yml).

El archivo [`package.json`](https://github.com/ppy/osu-wiki/blob/master/package.json) lista todos los complementos usados por el CI, de los cuales algunos fueron escritos por los administradores de la osu! wiki.

Las comprobaciones de CI se ejecutan automáticamente en cada confirmación de un colaborador recurrente. Para unir las 'pull request' , se espera que los contribuidores arreglen errores reportados por el CI. Para ver el [estado de verificación](img/ci-status.png), haz lo siguiente:

1. Desplácese hacia abajo la pagina de 'pull request' 
2. Scroll down the pull request's page, find the `osu-wiki continuous integration` status row, and click the `Details` link.
3. On the new page, expand the `run remark on changed files` step. Each finding is accompanied by its exact location in a file and a short description of why it is an error.

If you need help with decrypting CI check errors, or fixing issues, ask in the `#osu-wiki` channel on Discord.

### Development

The osu! wiki is integrated into the osu! website, which means all technical feature requests should be [made and tracked](https://github.com/ppy/osu-web/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc+label%3Aarea%3Awiki) in the `ppy/osu-web` repository. To inform other contributors of your request, make sure to link the issue in the `#osu-wiki` Discord channel, or the osu! wiki's issue tracker.

### Tools

Some features are not directly related to the osu! website, but may be useful for contributing or general housekeeping. In this case, they are implemented by people capable of it and are **not** added to the website directly:

- [osu-wiki status](https://clayton.cc/osu-wiki-status/en): list of articles per language, and the category of maintenance they require (translation, update, stub expansion). See [ppy/osu-wiki#2486](https://github.com/ppy/osu-wiki/issues/2486) for functionality requests.
- [osu-wiki-bin](https://github.com/cl8n/osu-wiki-bin): a Node.js utility for automated checks and edits (broken links, usergroup updates, wiki-wide text replacements, among other things)
- [flag-wiki-osu](https://megaapplepi.github.io/flag-wiki-osu): automatically add references to the flags mentioned in an article. See [ppy/osu-wiki#328](https://github.com/ppy/osu-wiki/issues/328) for functionality requests.

## Routines

*Note: the [osu-wiki status](https://clayton.cc/osu-wiki-status/en) website shows a list of all articles in need of maintenance, broken down by category.*

The wiki relies on input from the osu! community. You can help the maintainers and other contributors by doing your part. For information on how to do that, read the [contribution guide](/wiki/osu!_wiki/Contribution_guide). If at any point you feel stuck, ask for help in the `#osu-wiki` channel of the [osu!dev Discord server](/wiki/Community/osu!dev_Discord_server).

### Translations

<!-- note: the GitHub links are intentional here, because they expose many articles of a category at once -->

*For a list of translations and their completeness, see: [osu-wiki status](https://clayton.cc/osu-wiki-status/en)*

The osu! wiki is read by people from all around the world. To help your local community and attract new awesome players, mappers, modders, and developers into the game, you can translate English articles, or update existing translations that have fallen behind. Check the [list of languages](/wiki/Article_styling_criteria/Formatting#locales) supported by the osu! wiki, and ensure your translation follows the [content parity](/wiki/Article_styling_criteria/Writing#content-parity) principle. If you are a fluent speaker and experienced writer, take on key topics such as articles on [rules](https://github.com/ppy/osu-wiki/tree/master/wiki/Rules) or the [ranking criteria](https://github.com/ppy/osu-wiki/tree/master/wiki/Ranking_Criteria). In case you are only beginning your writing career, pick a small article to receive help and guidance from native reviewers.

A translation may be merged without a native review if it has been more than two weeks since its creation date.

### Stub expansion

*For possible scope of work, see: [List of existing stubs (English)](https://github.com/search?q=stub%3A+true+repo%3Appy%2Fosu-wiki+filename%3Aen.md)*

Some articles of the osu! wiki are incomplete and lack information. Such articles are marked as *stubs*, which means that they are important enough to exist as individual pages, but will be completed later. If you are familiar with the topic of the article, contribute to it and share your knowledge.

### Cross-linking

One of the key features of any wiki is *connectivity*, meaning that articles refer to related pages, helping a reader stay in the flow. To connect the articles, add links to mentioned terms where it is important for a better understanding of the subject. Link to individual sections of the article when necessary, and use [disambiguation pages](/wiki/Article_styling_criteria/Formatting#disambiguation-articles) for blanket terms.

### New articles

osu! is an ever-changing environment: the community makes new beatmaps, invents new ways of self-expression, and does other *new* things. If a certain event or term is not covered, do not hesitate to write an article about it and contribute to the pool of global knowledge. New tournament or contest? New osu! feature? Unknown part of the lore? Put your sharp writing skills to good use.

### Updates

*For possible scope of work, see: [List of untracked TODOs (English)](https://github.com/search?q=TODO+repo%3Appy%2Fosu-wiki+filename%3Aen.md)*

Existing articles need maintenance too. If you have found a factual error, or there are details missing, or if you simply want to rewrite/expand the article according to the reality, step forward and make the osu! wiki a better place. In case the change you plan is large or significant enough, make sure to bring it up for discussion in the `#osu-wiki` channel, or [create a tracking issue](https://github.com/ppy/osu-wiki/issues/new).
