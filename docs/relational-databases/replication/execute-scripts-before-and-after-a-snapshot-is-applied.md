---
title: スナップショットが適用される前および後のスクリプトの実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], scripts
- scripts [SQL Server replication], snapshots
- snapshot replication [SQL Server], scripts
ms.assetid: b7bb1e4c-5b48-4bb1-9dc8-47c911f2cc82
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 59a73607859d9c1858f09698dc30aee9d018ce26
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851110"
---
# <a name="execute-scripts-before-and-after-a-snapshot-is-applied"></a>スナップショットが適用される前および後のスクリプトの実行
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、スナップショットの適用前または適用後に実行するオプションのスクリプトを指定します。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
> [!NOTE]  
>  **[スナップショットの形式]** が **[文字]** に設定されている場合、これらのオプションは利用できません。  
  
### <a name="to-execute-a-script-before-or-after-a-snapshot-is-applied"></a>スナップショット適用前または適用後にスクリプトを実行するには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、以下の操作を実行します。  
  
    -   スナップショット適用前に実行するスクリプトを指定するには、 **[参照]** をクリックしてスクリプトに移動するか、 **[スナップショットの適用前に以下のスクリプトを実行]** ボックスにスクリプトへのパスを入力します。  
  
        > [!NOTE]  
        >  ディストリビューション エージェントまたはマージ エージェントは、指定するディレクトリに対し、読み取り権限を持つ必要があります。 プル サブスクリプションを使用する場合は、共有ディレクトリを UNC (汎用名前付け規則) パス (\\\computername\scripts\myscript.sql など) で指定する必要があります。  
  
    -   スナップショット適用後に実行するスクリプトを指定するには、 **[参照]** をクリックしてスクリプトに移動するか、 **[スナップショットの適用後に以下のスクリプトを実行]** ボックスにスクリプトへの UNC パスを入力します。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [スナップショットのプロパティの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [パブリケーションとアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [スナップショットが適用される前および後のスクリプトの実行](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
