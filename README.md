const readmeGenerator = (template: CanvasSection[], settings: Settings) => {
  const readme = template.reduce((readme, section) => {
    if (section.props.state === CanvasStatesEnum.ALERT) return readme;
    const { state, styles } = section.props;

    if (state === CanvasStatesEnum.ALERT) return readme;

    const generator = (sectionsGeneratorMap as any)[section.type!];

    if (!generator) return readme;

    const html = htmlPrettify(generator(section.props, settings));

    return `${readme}\n${html}\n###`;
    return `${readme}\n${
      styles.clear ? '\n<br clear="both">\n' : ''
    }\n${html}\n###`;
  }, '');

  const readmeFormated = readme.replace(/(###)/g, '\n$1');
