---
title: 'タスク 5: 用語ベースのリレーションシップを設定する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5f10c82ef5e0b63e0b81b630ed0340545c876661
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064738"
---
# <a name="task-5-setting-term-based-relationships"></a>タスク 5: 用語ベースのリレーションを設定する
  このタスクでは、 **Supplier Name**ドメインの値に対して用語ベースのリレーションをいくつか定義します。 用語ベースのリレーションを使用すると、ドメインの値の一部になっている用語を修正できます。 用語ベースのリレーションでは、共通する部分のスペルを除いても同一である複数の値は同一のシノニムと見なすことができます。 たとえば、 **Inc**は、を**組み込む**ように修正できます。 DQS では、ナレッジの検出、クレンジング、または照合プロセスでこれらのリレーションを使用します。 詳細については[、「用語ベースのリレーションを作成する](https://msdn.microsoft.com/library/hh510404.aspx)」を参照してください。  
  
1.  [**ドメイン] ボックスの一覧**で [ **Supplier Name** ] を選択します。  
  
2.  右側のペインの [**用語ベースの関係**] タブに切り替えます。  
  
3.  ツールバーの [**新しいリレーションシップの追加**] ボタンをクリックして、テーブルにリレーションを追加します。  
  
4.  [**値**] フィールドに「 **Co** 」と入力し、[**宛先**] フィールドに「 **Company** 」と入力します。  
  
5.  次の値ごとに、上記 2 つの手順を繰り返します。  
  
    |値|次に修正|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![用語ベースのリレーション](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "用語ベースのリレーション")  
  
## <a name="next-step"></a>次の手順  
 [タスク 6: シノニムを設定する](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  
