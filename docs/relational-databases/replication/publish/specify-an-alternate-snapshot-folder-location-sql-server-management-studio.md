---
title: "代替スナップショット フォルダーの場所の指定 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 9293f0eb-5531-47ec-b6e2-0392823ce5cc
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d848053cc583e27c473f651a5a9d52039d4f8cbd
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="specify-an-alternate-snapshot-folder-location-sql-server-management-studio"></a>代替スナップショット フォルダーの場所の指定 (SQL Server Management Studio)
  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、代替スナップショット フォルダーの場所を指定します。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
### <a name="to-specify-an-alternate-snapshot-location"></a>スナップショットの代替位置を指定するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、以下の操作を実行します。  
  
    1.  **[ファイルを次のフォルダーに保存する]**チェック ボックスをオンにし、 **[参照]** をクリックしてディレクトリに移動するか、スナップショット ファイルの格納先ディレクトリへのパスを入力します。  
  
        > [!NOTE]  
        >  スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\computername\snapshot など) で指定する必要があります。 詳細については、「[スナップショット フォルダーのセキュリティ保護](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)」を参照してください。  
  
    2.  スナップショット ファイルを既定のフォルダーにも書き込む必要がない限り、 **[ファイルを既定のフォルダーに保存する]** チェック ボックスはオフにしてください。  
  
     スナップショット ファイルを圧縮するには、 **[スナップショット ファイルをこのフォルダーに圧縮]**を選択します。 圧縮は通常、低帯域幅接続を使用する場合や、スナップショットの代替位置をリムーバブル メディア (CD-ROM など) にする場合に使用します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [スナップショット フォルダーの代替位置](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [スナップショットのプロパティの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [既定のスナップショットの場所の指定 &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
