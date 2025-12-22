# Image-to-Code Workflow (Multimodal)

One of the biggest challenges engineers face is describing UI designs in text. OpenCode solves this with the **@multimodal-looker** agent.

This feature allows you to save design images (screenshots/mockups) in a local folder, then instruct the AI to convert them into clean React/Next.js code.

## Steps

### 1. Prepare Images
Save your design reference images in the project folder.
* Example: Create an `assets` folder in the project root, then save the image as `design-ref.png`.
* Path: `./assets/design-ref.png`

### 2. Run the Special Prompt
Use the prompt below. This prompt has been optimized for the **Next.js App Router** and **Clean Code** (Atomic Design) standards.

**Copy to OpenCode Terminal:**

```text
@multimodal-looker Please analyze the design image in ./assets/design-ref.png in depth.

I want you to implement the design using:
- Framework: Latest version of Next.js (App Router)
- Language: TypeScript
- Styling: Tailwind CSS
- Icon: Lucide React (if any icons)

Please work according to good Software Engineering standards:
1. Component Structure: Break down the UI into small, reusable components (atomic design). Do not put all the code in one page.tsx file.
2. Rendering: Use Server Components (RSC) by default. Only add the “use client” directive to small components that require state or interactivity.
3. Responsiveness: Ensure responsive implementation (mobile-first approach).
4. Code Quality: Use semantic HTML and ensure TypeScript data types are clearly defined (avoid ‘any’).

Please create the folder structure first, then generate the code.
```

### 3. Why is this prompt effective?
* **`@multimodal-looker`**: Forces the use of the Vision model (Gemini 3 Pro) to “see” local images.
* **Stack Lock**: Locks the technology to the Next.js App Router so it doesn't get outdated code (Pages router).
* **RSC First**: Reminds AI to prioritize performance (Server Components).