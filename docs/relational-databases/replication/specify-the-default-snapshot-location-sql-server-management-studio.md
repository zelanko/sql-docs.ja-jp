---
title: "既定のスナップショットの場所の指定 (SQL Server Management Studio) | Microsoft Docs"
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
- snapshots [SQL Server replication], default locations
- default snapshot locations
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e6cda346b9dfdbc0a5693ce263456ee7f10076a2
ms.lasthandoff: 04/11/2017

---
# <a name="specify-the-default-snapshot-location-sql-server-management-studio"></a>既定のスナップショットの場所の指定 (SQL Server Management Studio)
  ディストリビューションの構成ウィザードの **[スナップショット フォルダー]** ページで、既定のスナップショットの場所を指定します。 ウィザードの使用の詳細については、「[パブリッシングおよびディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)」を参照してください。 ディストリビューターとして構成されていないサーバーでパブリケーションを作成する場合は、パブリケーションの新規作成ウィザードの **[スナップショット フォルダー]** ページで既定のスナップショットの場所を指定します。 このウィザードの使用の詳細については、「[パブリケーションの作成](../../relational-databases/replication/publish/create-a-publication.md)」を参照してください。  
  
 **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[パブリッシャー]** ページで、既定のスナップショットの場所を変更します。 詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)」を参照してください。 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで、各パブリケーションのスナップショット フォルダーを設定します。 詳しくは、「 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」をご覧ください。  
  
### <a name="to-modify-the-default-snapshot-location"></a>既定のスナップショットの場所を変更するには  
  
1.  **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[パブリッシャー]** ページで、既定のスナップショットの場所を変更するパブリッシャーのプロパティ ボタン (**[...]**) をクリックします。  
  
2.  **[パブリッシャーのプロパティ - \<Publisher>]** ダイアログ ボックスで、**[既定のスナップショット フォルダー]** プロパティの値を入力します。  
  
    > [!NOTE]  
    >  スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\computername\snapshot など) で指定する必要があります。 詳細については、「[スナップショット フォルダーのセキュリティ保護](../../relational-databases/replication/security/secure-the-snapshot-folder.md)」を参照してください。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [スナップショット フォルダーの代替位置](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
