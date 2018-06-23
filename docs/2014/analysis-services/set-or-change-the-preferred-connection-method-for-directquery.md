---
title: 設定または DirectQuery の優先接続方法を変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f10d5678-d678-4251-8cce-4e30cfe15751
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bf6abf3e4576fb28155529ee1bdfd24520176010
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176486"
---
# <a name="set-or-change-the-preferred-connection-method-for-directquery"></a>DirectQuery の優先接続方法の設定または変更
  DirectQuery モードで使用するモデルを作成する場合は、まず、DirectQuery の使用をサポートするようにデザイン環境を構成する必要があります。 これを行うには、次を参照してください。 [DirectQuery デザイン モードを有効にする&#40;SSAS 表形式&#41;](tabular-models/enable-directquery-mode-in-ssdt.md)です。  
  
 モデルを配置する準備ができたら、追加のプロパティを設定して、ユーザーが DirectQuery モードの 1 つを使用してモデルにアクセスできるようにする必要があります。  
  
-   モデルに対するクエリでキャッシュ データとリレーショナル データ ソースのどちらを使用する必要があるかを指定する必要があります。 ハイブリッド モードまたは DirectQuery のみを使用できます。  
  
-   パーティションを使用している場合は、DirectQuery データ ソースとして使用するパーティションを指定する必要があります。  
  
-   SQL Server データ ソースにアクセスするユーザーの権限借用オプションを設定する必要があります。  
  
 この手順では、デザイナーで DirectQuery モデルの優先接続方法を設定する方法について説明します。 モデルの配置後に [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] でこのプロパティを変更する方法についても説明します。  
  
### <a name="to-set-the-preferred-connection-method-for-a-directquery-model"></a>DirectQuery モデルの優先接続方法を設定するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、DirectQuery モデルのソリューション ファイルを開きます。  
  
2.  Visual Studio で、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
3.  **[プロパティ]** ペインで、 **DirectQueryMode**プロパティを、DirectQuery の使用をサポートする値の 1 つに変更します。  
  
    -   **インメモリ (DirectQuery あり)**: このオプションを使用する場合、モデルは配置されますが、モデルに対してクエリを実行する前にキャッシュを処理する必要があります。  
  
    -   **DirectQuery (インメモリあり)**: このオプションを使用する場合、キャッシュは既に処理されている場合にクライアントで使用可能になります。 この設定でモデルを配置し、キャッシュを処理しない場合、一部のクライアントではモデルに接続しようとするとエラーが発生します。  
  
    -   **DirectQuery のみ**: このオプションを使用する場合、メタデータは配置されますが、モデルにはデータがありません。 インメモリ モードを使用して接続しようとするクライアントでは、モデルが存在しないか処理されていないことを示すエラーが発生します。  
  
4.  エラーがある場合は、Visual Studio で **[エラー一覧]** を開き、モデルが DirectQuery モードで配置されるのを妨げている問題を解決します。  
  
### <a name="to-verify-or-change-the-preferred-connection-method-for-a-directquery-model"></a>DirectQuery モデルの優先接続方法を検証または変更するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] で、DirectQuery モデルを配置したインスタンスに接続します。  
  
2.  モデル データベースを右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[プロパティ]** ペインで、 **DirectQueryMode**プロパティを次のいずれかの値に変更します。  
  
    -   **DirectQuery のみ**  
  
    -   **インメモリ (DirectQuery あり)**  
  
    -   **DirectQuery (インメモリあり)**  
  
 これらのプロパティは、配置前に Visual Studio でプロジェクトに設定したプロパティと同じです。 DirectQuery の使用をサポートするようにモデルを構成してあれば、DirectQuery モードの優先接続方法をいつでも変更できます。  
  
## <a name="see-also"></a>参照  
 [DirectQuery モード &#40;SSAS テーブル&#41;](tabular-models/directquery-mode-ssas-tabular.md)   
 [DirectQuery デザイン モードを有効にする&#40;SSAS 表形式&#41;](tabular-models/enable-directquery-mode-in-ssdt.md)  
  
  