---
title: "SuMaEM: Efficient LiDAR-based Semantic SLAM with EM ICP"
excerpt: "Improved the original Semantic ICP in SuMa ++ with Semantic ICP through Expectation-Maximization<br/><img src='/images/suma/suma.png' width='600'>"
collection: projects
---

- Author: LIN JIANING

- Date: 2020.2 - 2020.4

- Environment: i7-8600k + GTX 1080

- Language: C++

## Abtract
We attempt to improve upon the existing ICP algorithm of SuMa++. We attempted to enhance the algorithm through Expectation-Maximization concepts. We mainly incorporated correntropy to utilize the last error of ICP and confusion matrix of labels to make full use of semantic associations. We evaluate our algorithm on KITTI Dataset and our experimental results show that adding correntropy does improve the performance when the paths are initially smooth because we maintain fewer effective points. Our methods will increase the error in some sequence with abrupt changes near the start of the path. However, adding confusion matrix of labels on top of correntropy can make the algorithm more stable, which makes our algorithm performs better in sequences with such rapid changes, i.e sequence 01.

## Videos
<iframe width="560" height="315" src="https://www.youtube.com/embed/GOJdxepvooA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Performance Comparison in KITTI Dataset Sequence 00
| Rotation Error | Translation Error |
| :------------: |:----------------: |
| ![rl](/images/suma/00_rl.png) | ![tl](/images/suma/00_tl.png) |

## More Details
Project Website: [http://www-personal.umich.edu/~zeph/sumaem.html](http://www-personal.umich.edu/~zeph/sumaem.html)

