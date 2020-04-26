---
title: 'タスク 8: 複合ドメインルールを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7e40ec982a9b2c43c3d55ec60179ac9a0b80e8a1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65489625"
---
# <a name="task-8-creating-a-composite-domain-rule"></a>タスク 8: 複合ドメイン ルールを作成する
  このタスクでは、 **Address Validation**複合ドメインのルールを作成します。 クロスドメインルールを定義する: **city**が**ロサンゼルス**の場合、 **state**は**CA**である必要があります。**市区町村**と**州**は2つのドメインです。  
  
1.  右側のウィンドウで、[CD の**規則**] タブに切り替えます。  
  
2.  ツールバーの [**新しいドメインルールの追加**] をクリックします。  
  
3.  [**名前**] に「 **City-State Rule** 」と入力し、 **enter**キーを押します。  
  
4.  [**ルールの作成**] ペインで、[ドメイン] ボックスの一覧の [ **City** ] を選択し、[条件**値が以下**] を選択して、値に「**ロサンゼルス**(ロサンゼルス)」と入力します。  
  
5.  **[Then** ] ペインで、[ドメイン] ボックスの一覧の [**状態**] を選択し、[**値が次の値に等しい**] を選択し、値として「 **CA** 」と入力して、 **tab**キーを押します。  
  
     ![複合ドメイン ルール](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "複合ドメイン ルール")  
  
6.  ページの下部にある [**閉じる**] ボタンをクリックして、DQS クライアントのメインページに切り替えます。 次のレッスンでナレッジ ベースをパブリッシュします。 ナレッジ ベースがロック状態 (ロック アイコン) にあることに注意してください。  
  
## <a name="next-step"></a>次の手順  
 [タスク 9: 参照データ サービスを構成する](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  
