---
title: Oracle テーブルスペースの管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 36616a0cfac49437274c991172cb05aed5a14b9b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301892"
---
# <a name="manage-oracle-tablespaces"></a>Oracle テーブルスペースの管理
  テーブルスペースは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のファイル グループにほぼ等しいデータベース領域の単位です。 テーブルスペースでは、個々のグループ内でデータベース オブジェクトの格納および管理が可能です。 詳細については Oracle のマニュアルを参照してください。  
  
 Oracle パブリケーションの一部としてテーブルを構成する場合、必要に応じて、レプリケーション ログ情報を格納するときに既存の Oracle テーブルスペースを使用するように指定できます。 指定しない場合、レプリケーション オブジェクトのテーブルスペースは、パブリッシャーの構成時に構成したレプリケーション管理ユーザー スキーマに関連付けられた既定のテーブルスペースとなります。  
  
 **アーティクルのログ テーブルのテーブルスペースを指定するには**   
  
-   **[アーティクルのプロパティ]** ダイアログ ボックスでテーブルスペースを指定します。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](../publish/view-and-modify-publication-properties.md)」を参照してください。  
  
-   [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) を使用します。 **sp_changearticle**を使用するには、以下を指定します。  
  
    -   パラメーター **@publisher**のファイル グループにほぼ等しいデータベース領域の単位です。  
  
    -   パラメーター **@publication**のファイル グループにほぼ等しいデータベース領域の単位です。  
  
    -   パラメーター **@article**のファイル グループにほぼ等しいデータベース領域の単位です。  
  
    -   パラメーター **@property**のファイル グループにほぼ等しいデータベース領域の単位です。  
  
    -   パラメーター **@value**のファイル グループにほぼ等しいデータベース領域の単位です。  
  
## <a name="see-also"></a>参照  
 [Configure an Oracle Publisher (Oracle パブリッシャーの構成)](configure-an-oracle-publisher.md)   
 [Objects Created on the Oracle Publisher](objects-created-on-the-oracle-publisher.md)  
  
  
