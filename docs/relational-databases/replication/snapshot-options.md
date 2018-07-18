---
title: スナップショット オプション | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
caps.latest.revision: 28
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c658f7898af62407a2c5458951aa14263ab94e7b
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353104"
---
# <a name="snapshot-options"></a>スナップショット オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  スナップショットを使用してサブスクリプションを初期化する際には、いくつかのオプションがあります。  
  
-   既定のスナップショット フォルダーを代替または追加する場所として、代替スナップショット フォルダーの場所を指定できます。 詳細については、「 [Alternate Snapshot Folder Locations](../../relational-databases/replication/alternate-snapshot-folder-locations.md)」を参照してください。  
  
-   リムーバブル メディア上に格納するためや低速なネットワーク上で転送するための圧縮スナップショットを使用できます。 詳細については、「 [Compressed Snapshots](../../relational-databases/replication/compressed-snapshots.md)」を参照してください。  
  
-   スナップショットを適用する前または後に、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを実行できます。 詳しくは、「[スナップショットが適用される前および後のスクリプトの実行](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)」をご覧ください。  
  
-   ファイル転送プロトコル (FTP) を使用してスナップショット ファイルを転送できます。 詳細については、「[FTP によるスナップショットの転送](../../relational-databases/replication/transfer-snapshots-through-ftp.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
