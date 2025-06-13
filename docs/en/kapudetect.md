# KaPU Detect

Chicken diseases are economically significant from their effects on chicken production, performance and some affect human (zoonotic). Chicken farming in Tanzania operates on small to medium scale managed by youths and women in peri-urban and rural areas. Farms are either backyard type or semi-intensive in deep litter.

The economic effects of chicken diseases are high mortality rates and failure to compete on the export market. Therefore, robust diagnostics are required for these diseases at farm level to improve chicken health.

KaPU Detect is an end to end tool that uses Artificial Intelligence (AI) for early diagnosis of three common chicken diseases namely Coccidiosis, Newcastle disease and Salmonella using images of chicken droppings. KaPU Detect is a component of KaPU application.

The figure below indicates the chicken droppings images for Coccidiosis, Newcastle and Salmonella diseases and Healthy chicken.

<figure>
    <img src ="/kapudocs/en/assets/fecal.png" alt="droppings" style="width:60%">
    <figcaption>Healthy and diseased chicken droppings images</figcaption>
</figure>

1. Coccidiosis is caused by parasites of the genus Eimeria that affect the intestinal tracts of chicken.

2. Newcastle disease is an acute viral infection in domestic chicken and other bird species caused by avian paramyxovirus serotype 1 (APMV-1).

3. Salmonella are bacterial pathogens of the genus Salmonella that cause diseases in chickens, animals and humans. 

A user takes a picture using the phone camera and the KaPU Detect classifies the disease by drawing a bounding box for the different classes of chicken droppings. The figure below indicates the detection of Coccidiosis disease by KaPu Detect.

<figure>
    <img src ="/kapudocs/assets/classify.jpg" alt="droppings" style="width:40%">
    <figcaption>Healthy and diseased chicken droppings images</figcaption>
</figure>

__Collect__ is an interface on KaPU app used to crowd-source new images of chicken droppings.
A user takes a photo using phone camera then provides a label of the image and uploads for storage on a remote server.  The figure below indicates the uploading of an image using the functionality.


<figure>
    <img src ="/kapudocs/assets/collect.jpg" alt="droppings" style="width:40%">
    <figcaption>Collecting new images of chicken droppings images</figcaption>
</figure>