---
{"aliases":null,"tags":null,"description":null,"title":"deducing this {C++23}","created":"2024-01-10T17:13:44","updated":"2024-01-10T17:15:52","dg-publish":true,"permalink":"/docs/deducing this {C++23}/","dgPassFrontmatter":true}
---

- [[docs/C++\|C++]]
- [microsoft.com/cppblog/C++23's Deducing this: what it is, why it is, how to use it](https://devblogs.microsoft.com/cppblog/cpp23-deducing-this/)
- 
---

## Bing Chat answer

Here is a summary of the page in Microsoft Edge:

- [**C++23’s Deducing this: what it is, why it is, how to use it**: The page is a blog post by Sy Brand, a C++ developer advocate, explaining the new feature of explicit object parameters in C++23, which allows specifying the implicit object parameter of a member function explicitly](https://edgeservices.bing.com/edgesvc/chat?udsframed=1&form=SHORUN&clientscopes=chat,noheader,udsedgeshop,channelstable,wincopilot,ntpquery,udsinwin11,udsdlpconsent,&shellsig=a195b9e450b2877bd3f359162004345394ec7a74&setlang=en-US&lightschemeovr=1#sjevt%7CDiscover.Chat.SydneyClickPageCitation%7Cadpclick%7C0%7Cf863cd2d-b94c-4518-9713-33e862ba2b9b%7C%7B%22sourceAttributions%22%3A%7B%22providerDisplayName%22%3A%22C%2B%2B23's%20De...%22%2C%22pageType%22%3A%22html%22%2C%22pageIndex%22%3A1%2C%22relatedPageUrl%22%3A%22https%253A%252F%252Fdevblogs.microsoft.com%252Fcppblog%252Fcpp23-deducing-this%252F%22%2C%22lineIndex%22%3A1%2C%22highlightText%22%3A%22C%2B%2B23's%20Deducing%20this%3A%20what%20it%20is%2C%20why%20it%20is%2C%20how%20to%20use%20it%20-%20C%2B%2B%20Team%20Blog%22%2C%22snippets%22%3A%5B%5D%7D%7D)[1](https://edgeservices.bing.com/edgesvc/chat?udsframed=1&form=SHORUN&clientscopes=chat,noheader,udsedgeshop,channelstable,wincopilot,ntpquery,udsinwin11,udsdlpconsent,&shellsig=a195b9e450b2877bd3f359162004345394ec7a74&setlang=en-US&lightschemeovr=1#sjevt%7CDiscover.Chat.SydneyClickPageCitation%7Cadpclick%7C0%7Cf863cd2d-b94c-4518-9713-33e862ba2b9b%7C%7B%22sourceAttributions%22%3A%7B%22providerDisplayName%22%3A%22C%2B%2B23's%20De...%22%2C%22pageType%22%3A%22html%22%2C%22pageIndex%22%3A1%2C%22relatedPageUrl%22%3A%22https%253A%252F%252Fdevblogs.microsoft.com%252Fcppblog%252Fcpp23-deducing-this%252F%22%2C%22lineIndex%22%3A1%2C%22highlightText%22%3A%22C%2B%2B23's%20Deducing%20this%3A%20what%20it%20is%2C%20why%20it%20is%2C%20how%20to%20use%20it%20-%20C%2B%2B%20Team%20Blog%22%2C%22snippets%22%3A%5B%5D%7D%7D).
- **Motivation**: The feature was motivated by the need to avoid code duplication and improve performance for member functions that need to handle different const/volatile/reference qualifiers of the object they are called on, such as std::optional::value.
- [**Design**: The feature follows the principle of doing what the user expects, and does not change the existing rules of overload resolution, template deduction, or name resolution](https://edgeservices.bing.com/edgesvc/chat?udsframed=1&form=SHORUN&clientscopes=chat,noheader,udsedgeshop,channelstable,wincopilot,ntpquery,udsinwin11,udsdlpconsent,&shellsig=a195b9e450b2877bd3f359162004345394ec7a74&setlang=en-US&lightschemeovr=1#sjevt%7CDiscover.Chat.SydneyClickPageCitation%7Cadpclick%7C1%7Cf863cd2d-b94c-4518-9713-33e862ba2b9b%7C%7B%22sourceAttributions%22%3A%7B%22providerDisplayName%22%3A%22Notably%2C%20w...%22%2C%22pageType%22%3A%22html%22%2C%22pageIndex%22%3A1%2C%22relatedPageUrl%22%3A%22https%253A%252F%252Fdevblogs.microsoft.com%252Fcppblog%252Fcpp23-deducing-this%252F%22%2C%22lineIndex%22%3A103%2C%22highlightText%22%3A%22Notably%2C%20we%20didn%E2%80%99t%20touch%20overload%20resolution%20rules%20or%20template%20deduction%20rules%2C%20and%20name%20resolution%20was%20only%20changed%20a%20little%20bit%20(as%20a%20treat).%22%2C%22snippets%22%3A%5B%5D%7D%7D)[2](https://edgeservices.bing.com/edgesvc/chat?udsframed=1&form=SHORUN&clientscopes=chat,noheader,udsedgeshop,channelstable,wincopilot,ntpquery,udsinwin11,udsdlpconsent,&shellsig=a195b9e450b2877bd3f359162004345394ec7a74&setlang=en-US&lightschemeovr=1#sjevt%7CDiscover.Chat.SydneyClickPageCitation%7Cadpclick%7C1%7Cf863cd2d-b94c-4518-9713-33e862ba2b9b%7C%7B%22sourceAttributions%22%3A%7B%22providerDisplayName%22%3A%22Notably%2C%20w...%22%2C%22pageType%22%3A%22html%22%2C%22pageIndex%22%3A1%2C%22relatedPageUrl%22%3A%22https%253A%252F%252Fdevblogs.microsoft.com%252Fcppblog%252Fcpp23-deducing-this%252F%22%2C%22lineIndex%22%3A103%2C%22highlightText%22%3A%22Notably%2C%20we%20didn%E2%80%99t%20touch%20overload%20resolution%20rules%20or%20template%20deduction%20rules%2C%20and%20name%20resolution%20was%20only%20changed%20a%20little%20bit%20(as%20a%20treat).%22%2C%22snippets%22%3A%5B%5D%7D%7D). [The explicit object parameter is distinguished by the keyword this before the type specifier, and can be a template parameter that is deduced from the expression used to call the member function](https://edgeservices.bing.com/edgesvc/chat?udsframed=1&form=SHORUN&clientscopes=chat,noheader,udsedgeshop,channelstable,wincopilot,ntpquery,udsinwin11,udsdlpconsent,&shellsig=a195b9e450b2877bd3f359162004345394ec7a74&setlang=en-US&lightschemeovr=1#sjevt%7CDiscover.Chat.SydneyClickPageCitation%7Cadpclick%7C2%7Cf863cd2d-b94c-4518-9713-33e862ba2b9b%7C%7B%22sourceAttributions%22%3A%7B%22providerDisplayName%22%3A%22The%20explic...%22%2C%22pageType%22%3A%22html%22%2C%22pageIndex%22%3A1%2C%22relatedPageUrl%22%3A%22https%253A%252F%252Fdevblogs.microsoft.com%252Fcppblog%252Fcpp23-deducing-this%252F%22%2C%22lineIndex%22%3A88%2C%22highlightText%22%3A%22The%20explicit%20object%20parameter%20is%20distinguished%20by%20the%20keyword%20thisplaced%20before%20the%20type%20specifier%2C%20and%20is%20only%20valid%20for%20the%20first%20parameter%20of%20the%20function.%22%2C%22snippets%22%3A%5B%5D%7D%7D)[3](https://edgeservices.bing.com/edgesvc/chat?udsframed=1&form=SHORUN&clientscopes=chat,noheader,udsedgeshop,channelstable,wincopilot,ntpquery,udsinwin11,udsdlpconsent,&shellsig=a195b9e450b2877bd3f359162004345394ec7a74&setlang=en-US&lightschemeovr=1#sjevt%7CDiscover.Chat.SydneyClickPageCitation%7Cadpclick%7C2%7Cf863cd2d-b94c-4518-9713-33e862ba2b9b%7C%7B%22sourceAttributions%22%3A%7B%22providerDisplayName%22%3A%22The%20explic...%22%2C%22pageType%22%3A%22html%22%2C%22pageIndex%22%3A1%2C%22relatedPageUrl%22%3A%22https%253A%252F%252Fdevblogs.microsoft.com%252Fcppblog%252Fcpp23-deducing-this%252F%22%2C%22lineIndex%22%3A88%2C%22highlightText%22%3A%22The%20explicit%20object%20parameter%20is%20distinguished%20by%20the%20keyword%20thisplaced%20before%20the%20type%20specifier%2C%20and%20is%20only%20valid%20for%20the%20first%20parameter%20of%20the%20function.%22%2C%22snippets%22%3A%5B%5D%7D%7D).
- [**Use Cases**: The page illustrates several use cases for the feature, such as de-duplication of code, CRTP, forwarding out of lambdas, recursive lambdas, passing this by value, and SFINAE-unfriendly callables](https://edgeservices.bing.com/edgesvc/chat?udsframed=1&form=SHORUN&clientscopes=chat,noheader,udsedgeshop,channelstable,wincopilot,ntpquery,udsinwin11,udsdlpconsent,&shellsig=a195b9e450b2877bd3f359162004345394ec7a74&setlang=en-US&lightschemeovr=1#sjevt%7CDiscover.Chat.SydneyClickPageCitation%7Cadpclick%7C3%7Cf863cd2d-b94c-4518-9713-33e862ba2b9b%7C%7B%22sourceAttributions%22%3A%7B%22providerDisplayName%22%3A%22These%20incl...%22%2C%22pageType%22%3A%22html%22%2C%22pageIndex%22%3A1%2C%22relatedPageUrl%22%3A%22https%253A%252F%252Fdevblogs.microsoft.com%252Fcppblog%252Fcpp23-deducing-this%252F%22%2C%22lineIndex%22%3A89%2C%22highlightText%22%3A%22These%20include%20de-quadruplication%20of%20code%2C%20recursive%20lambdas%2C%20passing%20thisby%20value%2C%20and%20a%20version%20of%20the%20CRTPwhich%20doesn%E2%80%99t%20require%20the%20base%20class%20to%20be%20templated%20on%20the%20derived%20class.%22%2C%22snippets%22%3A%5B%5D%7D%7D)[4](https://edgeservices.bing.com/edgesvc/chat?udsframed=1&form=SHORUN&clientscopes=chat,noheader,udsedgeshop,channelstable,wincopilot,ntpquery,udsinwin11,udsdlpconsent,&shellsig=a195b9e450b2877bd3f359162004345394ec7a74&setlang=en-US&lightschemeovr=1#sjevt%7CDiscover.Chat.SydneyClickPageCitation%7Cadpclick%7C3%7Cf863cd2d-b94c-4518-9713-33e862ba2b9b%7C%7B%22sourceAttributions%22%3A%7B%22providerDisplayName%22%3A%22These%20incl...%22%2C%22pageType%22%3A%22html%22%2C%22pageIndex%22%3A1%2C%22relatedPageUrl%22%3A%22https%253A%252F%252Fdevblogs.microsoft.com%252Fcppblog%252Fcpp23-deducing-this%252F%22%2C%22lineIndex%22%3A89%2C%22highlightText%22%3A%22These%20include%20de-quadruplication%20of%20code%2C%20recursive%20lambdas%2C%20passing%20thisby%20value%2C%20and%20a%20version%20of%20the%20CRTPwhich%20doesn%E2%80%99t%20require%20the%20base%20class%20to%20be%20templated%20on%20the%20derived%20class.%22%2C%22snippets%22%3A%5B%5D%7D%7D). The page also provides code examples and links to other resources for more information.