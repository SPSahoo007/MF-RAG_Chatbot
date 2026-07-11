# Disclaimer Snippet

The following disclaimer is hardcoded into the frontend UI footer (`templates/index.html`) to ensure users are aware that the assistant provides factual data only, and not financial advice.

```html
<p class="text-xs text-center text-gray-400 mt-4">
    AI-GENERATED CONTENT. STRICTLY FOR EDUCATIONAL PURPOSES. CONSULT A SEBI-REGISTERED FINANCIAL ADVISOR BEFORE INVESTING.
</p>
```

Additionally, the LLM is instructed via the System Prompt to append safe-refusal messages to any advisory queries, directing users to AMFI and SEBI resources.
