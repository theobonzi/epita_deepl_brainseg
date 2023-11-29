# Segmentation de Structures Cérébrales dans des IRM Cérébrales 3D

## Introduction
Ce projet porte sur la segmentation des structures cérébrales fondamentales dans des scans IRM 3D de cerveaux d'infants. Il utilise les données et le contexte du challenge [iSeg de la conférence MICCAI 2017](https://iseg2017.web.unc.edu).

> "The first year of life is a dynamic phase of postnatal brain development, characterized by rapid tissue growth and the development of cognitive and motor functions. This early period is crucial in many neurodevelopmental and neuropsychiatric disorders, such as schizophrenia and autism.
> 
> Accurate segmentation of infant brain MRI images into white matter (WM), gray matter (GM), and cerebrospinal fluid (CSF) during this critical period is fundamental to studying both normal and abnormal brain development. There are three distinct phases in the first-year brain MRI, including the infantile phase (≤ 5 months), the isointense phase (6-8 months), and the early adult-like phase (≥ 9 months). In the isointense phase, the intensity range of voxels in GM and WM largely overlaps, thus posing the most significant challenge for tissue segmentation."

## Objectif
Développer un système capable de segmenter avec précision les images IRM en identifiant différentes parties du cerveau, une tâche importante pour comprendre le développement cérébral chez les jeunes enfants.

## Approche de Segmentation
Pour atteindre cet objectif, j'utilise le réseau de neurones [U-Net](https://paperswithcode.com/method/u-net), une architecture profonde spécialement conçue pour la segmentation d'images médicales.

## Données
- **Ensemble d'entraînement** : Comprend des scans IRM avec des annotations manuelles.
- **Ensemble de test** : Contient des scans IRM à segmenter, sans annotations.

## Étapes Générales du Projet
1. **Comprendre les Données** : Explorer et visualiser les scans IRM.
2. **Préparer les Données** : Organiser les données pour le traitement.
3. **Construire et Entraîner le Modèle** : Développer un modèle pour la segmentation.
4. **Traiter et Soumettre les Résultats** : Appliquer le modèle sur l'ensemble de test et soumettre les résultats.

## Pour aller plus loin

### Amélioration de la Précision de Segmentation
Nous pouvons envisager plusieurs stratégies pour augmenter la précision de notre segmentation des scans IRM 3D :

1. **Système de Vote pour Chaque Pixel** :
   - Pour chaque pixel, nous examinons sa prédiction dans les trois tranches de l'image IRM 3D.
   - Un système de vote est utilisé pour déterminer la classe finale du pixel, en se basant sur la majorité des prédictions obtenues pour les différentes tranches.
   - Cette approche vise à exploiter les informations 3D disponibles dans les scans IRM.

2. **Analyse des Pixels Voisins** :
   - Pour accroître la précision, nous pouvons considérer les pixels voisins d'un pixel donné.
   - L'hypothèse est qu'un pixel a une forte probabilité d'appartenir à la même classe que la majorité de ses voisins.
   - Cette stratégie permet d'intégrer le contexte local et de réduire les erreurs de segmentation, notamment dans les zones où les structures cérébrales sont étroitement entrelacées.
