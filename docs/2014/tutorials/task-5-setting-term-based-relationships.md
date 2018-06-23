---
title: 'タスク 5: 用語ベースの設定の関係 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b8450d3e77de578810bb57c35aafad6f90c8f19c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070293"
---
# <a name="task-5-setting-term-based-relationships"></a>タスク 5: 用語ベースのリレーションを設定する
  このタスクでの値について、いくつかの用語ベースのリレーションを定義する、 **Supplier Name**ドメイン。 用語ベースのリレーションを使用すると、ドメインの値の一部になっている用語を修正できます。 用語ベースのリレーションでは、共通する部分のスペルを除いても同一である複数の値は同一のシノニムと見なすことができます。 たとえば、 **Inc.** を修正できる**Incorporated**です。 DQS では、ナレッジの検出、クレンジング、または照合プロセスでこれらのリレーションを使用します。 参照してください[作成用語ベースのリレーション](http://msdn.microsoft.com/library/hh510404.aspx)詳細についてはします。  
  
1.  選択**Supplier Name**で、**ドメイン リスト**です。  
  
2.  切り替えて、**用語ベースのリレーション**右ペインでタブです。  
  
3.  をクリックして**新しいリレーションシップの追加**テーブルにリレーションシップを追加するには、ツールバーのボタンをクリックします。  
  
4.  型**co.** の**値**フィールドと**会社**の**に修正**フィールドです。  
  
5.  次の値ごとに、上記 2 つの手順を繰り返します。  
  
    |値|次に修正|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![用語ベースのリレーション](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "用語ベースのリレーション")  
  
## <a name="next-step"></a>次の手順  
 [タスク 6: シノニムを設定する](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  