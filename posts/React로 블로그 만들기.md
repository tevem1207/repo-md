---
title: "React로 블로그 만들기"
createdAt: "2025-03-19T12:34:56Z"
pinned: true
tags: ["react", "nextjs", "github-api"]
---

# React로 블로그 만들기 🚀

GitHub API를 활용해 블로그를 만드는 방법에 대해 알아봅니다.

## 1. 프로젝트 구성
먼저 GitHub API에서 마크다운 데이터를 불러오는 함수를 작성해야 합니다.

```ts
import matter from "gray-matter";

export async function fetchPost(slug: string) {
  const fileUrl = `https://raw.githubusercontent.com/user/repo/main/posts/${slug}.md`;
  const res = await fetch(fileUrl);
  const rawMarkdown = await res.text();
  
  const { data, content } = matter(rawMarkdown);

  return { ...data, content };
}
