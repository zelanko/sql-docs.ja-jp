---
title: 'タスク 10: 参照データサービスを使用するように複合ドメインを構成する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 525e0286d8d82f501981c9e936caca581886b9b4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65481236"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>タスク 10: 参照データ サービスを使用して複合ドメインを構成する
  このタスクでは、 **Melissa Check**サービスを使用するように**Address Validation**複合ドメインを構成します。 実行時のクレンジング アクティビティでは、クレンジングのために Address Validation ドメインのドメイン値が DQS からこのサービスに渡されます。 詳細については、「[参照データへのドメインまたは複合ドメインのマップ」を](https://msdn.microsoft.com/library/hh213030.aspx)参照してください。  
  
1.  **DQS クライアント**のメインページで、[**最近使用したナレッジベース**] の下の [**サプライヤー (ドメイン管理)** ] をクリックして、[**ドメイン管理**] ページを起動します。  
  
2.  **ドメインの一覧**で [**アドレス検証**複合ドメイン] を選択します。  
  
3.  右ペインで、[**参照データ**] タブに切り替えます。  
  
     ![[参照データ] タブ](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "[参照データ] タブ")  
  
4.  ツールバーの [**参照**] ボタンをクリックします。  
  
5.  [**オンライン参照データプロバイダーのカタログ**] ダイアログボックスで、 **Melissa**の横の**チェックボックス**をオンにします。  
  
     ![[メリッサ データ - アドレスをチェック] の選択](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "[メリッサ データ - アドレスをチェック] の選択")  
  
6.  右側のウィンドウの [**スキーマ**] セクションで、ドロップダウンリストを使用して**アドレス行**ドメインを**アドレス行 (M)** スキーマ項目にマップします。  
  
     ![RDS スキーマのアイテムをドメインにマップ](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "RDS スキーマのアイテムをドメインにマップ")  
  
7.  ツールバーの [**スキーマエントリの追加] (+)** ボタンをクリックして、一覧にエントリを作成します。  
  
     ![[スキーマ エントリの追加] ツール バー ボタン](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "[スキーマ エントリの追加] ツール バー ボタン")  
  
8.  次の図に示すように、ドロップダウン リストを使用して次の DQS ドメインをマップします。  
  
     ![RDS スキーマ項目をドメインにマップする](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "RDS スキーマ項目をドメインにマップする")  
  
9. **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 11: ナレッジ ベースをパブリッシュする](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
