<%*
// Convert Title into URL Slug
  const slug = tp.frontmatter.title
    .toLowerCase()
    .replace(/[^\w\s]/gi, '') // Remove non-alphanumeric characters
    .replace(/\s+/g, '-') // Replace spaces with hyphens
    .trim(); // Remove any leading or trailing whitespace
  await tp.file.rename(slug);
-%>