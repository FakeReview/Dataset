### Introduction

There are a total of two datasets included here, namely CR-Dataset and CR-Dataset-CD, which are collectively referred to as Fake Review Dataset. CR-Dataset contains a total of 12,506 reviews from 10 different developed cities (excluding Chengdu), and CR-Dataset-CD contains a total of 5,600 reviews from Chengdu. The sensitive and private information in the datasets is hidden, mainly including user_name and shop_name. Each dataset consists of two files, which are review metadata and review text. Among them, the information contained in the review metadata is very rich, including id (a unique number for each review), label (1 indicates a fake review, and 0 indicates a truthful review), user_name (md5 with id-salt), shop_name (md5 with id-salt), vip (whether the user is a VIP), discount (whether the review has a certification tag - usually associated with a discount), overall (overall rating), taste (taste rating), environment (environment rating), service (service rating), ingredient (ingredient rating), consumption (consumption amount, and 0 indicates it is not given), food (number of recommended food), picture (number of posted pictures), like (number of likes), response (whether the review is responded by the merchant), interaction (the number of interactions with the review), time (the post time of the review). All these reviews are from the Dianping platform, a Chinese review community, and annotated through labeling rules.

Here are some examples of reviews in CR-Dataset. All review samples in Fake Review Dataset have the same format as the examples.

| id   | label | user_name                        | shop_name                        | vip  | discount | overall | taste | environment | service | ingredient | consumption | food | picture | like | response | interaction | time                |
| ---- | ----- | -------------------------------- | -------------------------------- | ---- | -------- | ------- | ----- | ----------- | ------- | :--------: | ----------- | ---- | ------- | ---- | -------- | ----------- | ------------------- |
| 6    | 0     | fa5657062d8e10144b503a7c94dffdc5 | 2bbf2e4486dd3ce19ebe33e57a99f09f | 1    | 1        | 4.0     | 4.0   | 4.0         | 4.0     |    4.0     | 64.0        | 3    | 0       | 0    | 0        | 0           | 2020-10-24 13:03:00 |
| 32   | 0     | 40410ee061183e2366c680f99faadc49 | 77046214892e9493f5831c046307a17a | 0    | 0        | 3.0     | 4.0   | 4.0         | 4.0     |    4.0     | 0.0         | 0    | 9       | 1    | 0        | 0           | 2019-10-01 08:24:00 |
| 74   | 0     | d336f5228c291c26df1e321ef60000c1 | cc88785052c5d05548ba43642ea2b79f | 1    | 1        | 4.5     | 4.0   | 4.5         | 4.5     |    4.5     | 0.0         | 0    | 10      | 0    | 1        | 1           | 2020-11-04 14:09:00 |
| 1478 | 1     | c14d0f8a623141e3d89eb064a08d8754 | 247ecac842d9101373397deb6a372c4d | 0    | 0        | 0.5     | 0.5   | 0.5         | 0.5     |    0.5     | 0.0         | 0    | 1       | 1    | 1        | 1           | 2020-10-28 21:16:00 |
| 1827 | 1     | 17029c1c2ebc419bda48f904cc9d8d6b | 7a52b08d82b2cd660e1298185debff6f | 1    | 1        | 4.5     | 5.0   | 4.5         | 5.0     |    5.0     | 80.0        | 0    | 6       | 1    | 1        | 1           | 2020-09-06 19:22:00 |
| 5526 | 1     | d0ead75dcd6abcb6e0a67ca94607e9eb | aaa703abf75e4f29ac316384a0c2e9f6 | 1    | 0        | 5.0     | 5.0   | 5.0         | 5.0     |    5.0     | 0.0         | 0    | 3       | 119  | 1        | 3           | 2020-03-11 23:26:00 |

| id   |                             text                             |
| :--- | :----------------------------------------------------------: |
| 6    | "环境还可以，晚上去的，也没排队，我们两个人，小桌没有了，直接给安排的6人长桌。上菜速度也挺快的，团的双人餐，两人吃还是够了，两个牛肉，几个素菜，一份红糖糍粑。糍粑好评，是现炸的，也比较软糯。牛肉有两种，偏瘦的比较有嚼劲，偏肥的比较好嚼，肉质都还不错。蘸料自助式的，我觉得自己配的还可以，我男朋友觉得酱料不太行。总体还是推荐" |
| 32   | "和朋友一起去的，因为当天感冒着，不让吃辣，就选了这么一家吃牛肉，总体来说还行吧，一来就喝了一碗汤，带着一点点牛肉的膻味，我不是很喜欢，没有偿出鲜美的感觉" |
| 74   | "工作日晚上人还蛮多的基本饭点要等位一小时吧。环境挺喜欢的，有氛围。冲着寿喜锅去的，没有很惊艳，有一丢丢低于预期。寿喜锅一上来上面是棉花糖，小哥会先询问要不要拍照，不然棉花糖就没啦！服务还是不错的。「融化鹅肝」「厚切嫩牛舌」「明太子烤土豆」都还挺推荐的。土豆会在你边上帮你烤，上面的酱不够也可以加的。" |
| 1478 | "真恶心，我带朋友去吃饭，服务员提出让我们换桌，结账后自己系统的问题没整明白，给我朋友打电话说没结账，会办人事吗？让别人怎么想我？祝关门大吉！" |
| 1827 | "食宝街二期，进大门右手边走楼梯上二楼，周末不到下午五点去的，已经有几桌了，环境布置的很有日式风格，最近推出的迷你丼很实惠，小小的碗下面是米饭，上面是菜，就是盖浇饭啦！尝试了海胆和鳗鱼，都很鲜甜！小碗其实刚刚好，不会浪费。大赞牛肉寿喜锅，新鲜的肥牛、白菜、魔芋丝、金针菇、茼蒿、豆腐满满的一锅，蘸上生鸡蛋，热乎乎满满的幸福感！炸鸡意外惊喜，外焦里嫩，火候刚刚好，两种蘸料，其中一种貌似沙拉酱上面撒的辣椒面，呵呵，很有创意，其实什么都不沾也很好吃！温泉蛋半熟，流动的蛋黄在口中蔓延，很香！大众点评9.9团100元券，点够200就可以用，相当于5.5折，还是很值的！服务员小姐姐态度特别好，帮到我很多，这个一定要大赞五分！" |
| 5526 | "广东清远鸡：精选国宴清远走地鸡，坐飞机而来的鸡，来头可不小，配上枸杞、香葱，不加多余的调味，却已是“鲜”气满满，让人为之感叹，咽一咽口水，静等八分钟，即可品尝。鲜活的鲍鱼，有八头鲍和四头鲍两种，更有“八一三”的吃法，八分钟锅底烧开，可以喝汤，品尝鸡肉，同时将鲍鱼翻面煮1分钟，关火再闷3分钟即可食用，这样的鲍鱼更鲜嫩Q弹，而且店内还贴心的准备了专用的小铲，现场将鲍鱼取出，现吃现取。" |



### Attention

Due to the sensitivity and privacy of Fake Review Dataset, I cannot directly publish the dataset. I show some samples of the dataset above and leave the contact information for readers to request the complete dataset.

If you are interested in the above data, please contact JYF ([jianyifei2@gmail.com](mailto:jianyifei2@gmail.com)) for Fake Review Dataset. I will send you an authorization (.pdf) that needs to be signed, which explains the restrictions on the use of the dataset. If you agree with the contents of the authorization, please sign and send it to me, and I will give you the complete dataset.
