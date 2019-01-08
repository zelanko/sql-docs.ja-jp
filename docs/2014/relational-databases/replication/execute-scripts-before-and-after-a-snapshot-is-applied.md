---
title: スナップショットが適用される前後にスクリプトの実行 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: f74130040c7344f881775b75718e1513f8879636
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52754044"
---
# <a name="execute-scripts-before-and-after-a-snapshot-is-applied-sql-server-management-studio"></a>スナップショット適用前および適用後のスクリプトの実行 (SQL Server Management Studio)
  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[スナップショット]** ページで、スナップショットの適用前または適用後に実行するオプションのスクリプトを指定します。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md)」を参照してください。  
  
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
 [スナップショットのプロパティの構成 &#40;レプリケーション Transact-SQL プログラミング&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [パブリケーションとアーティクルのプロパティの変更](publish/change-publication-and-article-properties.md)   
 [スナップショットが適用される前および後のスクリプトの実行](execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [スナップショットを使用したサブスクリプションの初期化](initialize-a-subscription-with-a-snapshot.md)  
  
  
