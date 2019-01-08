---
title: 既定のスナップショットの場所の指定 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], default locations
- default snapshot locations
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cd41dabe1554bc3f80adc4fdb6d8433f8aac9e7f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52807334"
---
# <a name="specify-the-default-snapshot-location-sql-server-management-studio"></a>既定のスナップショットの場所の指定 (SQL Server Management Studio)
  ディストリビューションの構成ウィザードの **[スナップショット フォルダー]** ページで、既定のスナップショットの場所を指定します。 ウィザードの使用の詳細については、「[パブリッシングおよびディストリビューションの構成](configure-publishing-and-distribution.md)」を参照してください。 ディストリビューターとして構成されていないサーバーでパブリケーションを作成する場合は、パブリケーションの新規作成ウィザードの **[スナップショット フォルダー]** ページで既定のスナップショットの場所を指定します。 このウィザードの使用の詳細については、「[パブリケーションの作成](publish/create-a-publication.md)」を参照してください。  
  
 **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[パブリッシャー]** ページで、既定のスナップショットの場所を変更します。 詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](view-and-modify-distributor-and-publisher-properties.md)」を参照してください。 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで、各パブリケーションのスナップショット フォルダーを設定します。 詳しくは、「 [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)」をご覧ください。  
  
### <a name="to-modify-the-default-snapshot-location"></a>既定のスナップショットの場所を変更するには  
  
1.  **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[パブリッシャー]** ページで、既定のスナップショットの場所を変更するパブリッシャーのプロパティ ボタン (**[...]**) をクリックします。  
  
2.  **[パブリッシャーのプロパティ - \<Publisher>]** ダイアログ ボックスで、**[既定のスナップショット フォルダー]** プロパティの値を入力します。  
  
    > [!NOTE]  
    >  スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\computername\snapshot など) で指定する必要があります。 詳細については、「[スナップショット フォルダーのセキュリティ保護](security/secure-the-snapshot-folder.md)」を参照してください。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [スナップショット フォルダーの代替位置](alternate-snapshot-folder-locations.md)   
 [スナップショットを使用したサブスクリプションの初期化](initialize-a-subscription-with-a-snapshot.md)  
  
  
