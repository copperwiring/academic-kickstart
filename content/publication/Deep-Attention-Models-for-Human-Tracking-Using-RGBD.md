---
title: " Deep Attention Models for Human Tracking Using RGBD "
authors:
- Maryamsadat Rasoulidanesh
- Srishti Yadav
- Sachini Herath
- Yasaman Vaghei
- Shahram Payandeh
date: "2019-01-01T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2019-01-01T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["2"]

# Publication name and optional abbreviated publication name.
publication: In *Special Issue "Depth Sensors and 3D Vision" of Multidisciplinary Digital Publishing Institute*
publication_short: In *MDPI*

abstract: Visual tracking performance has long been limited by the lack of better appearance models. These models fail either where they tend to change rapidly, like in motion-based tracking, or where accurate information of the object may not be available, like in color camouflage (where background and foreground colors are similar). This paper proposes a robust, adaptive appearance model which works accurately in situations of color camouflage, even in the presence of complex natural objects. The proposed model includes depth as an additional feature in a hierarchical modular neural framework for online object tracking. The model adapts to the confusing appearance by identifying the stable property of depth between the target and the surrounding object(s). The depth complements the existing RGB features in scenarios when RGB features fail to adapt, hence becoming unstable over a long duration of time. The parameters of the model are learned efficiently in the Deep network, which consists of three modules:(1) The spatial attention layer, which discards the majority of the background by selecting a region containing the object of interest; (2) the appearance attention layer, which extracts appearance and spatial information about the tracked object; and (3) the state estimation layer, which enables the framework to predict future object appearance and location. Three different models were trained and tested to analyze the effect of depth along with RGB information. Also, a model is proposed to utilize only depth as a standalone input for tracking purposes. The proposed models were also evaluated in real-time using KinectV2 and showed very promising results. The results of our proposed network structures and their comparison with the state-of-the-art RGB tracking model demonstrate that adding depth significantly improves the accuracy of tracking in a more challenging environment (i.e., cluttered and camouflaged environments). Furthermore, the results of depth-based models showed that depth data can provide enough information for accurate tracking, even without RGB information. 

tags:
- Source Themes
featured: true

links:
url_pdf: https://www.mdpi.com/1424-8220/19/4/750/pdf

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/pLCdAaMFLTE)'
  focal_point: ""
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects:
- internal-project

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: example
---

<!-- {{% alert note %}}
Click the *Cite* button above to demo the feature to enable visitors to import publication metadata into their reference management software.
{{% /alert %}}

{{% alert note %}}
Click the *Slides* button above to demo Academic's Markdown slides feature.
{{% /alert %}}

Supplementary notes can be added here, including [code and math](https://sourcethemes.com/academic/docs/writing-markdown-latex/). -->
