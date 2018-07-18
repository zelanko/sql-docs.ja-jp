---
title: スナップショット オプション | Microsoft Docs
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
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
caps.latest.revision: 27
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f6780cd434f8aa1bf35f08905fb41ec7cb652407
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152573"
---
# <a name="snapshot-options"></a>スナップショット オプション
  スナップショットを使用してサブスクリプションを初期化する際には、いくつかのオプションがあります。  
  
-   既定のスナップショット フォルダーを代替または追加する場所として、代替スナップショット フォルダーの場所を指定できます。 詳細については、「 [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md)」を参照してください。  
  
-   リムーバブル メディア上に格納するためや低速なネットワーク上で転送するための圧縮スナップショットを使用できます。 詳細については、「 [Compressed Snapshots](compressed-snapshots.md)」を参照してください。  
  
-   スナップショットを適用する前または後に、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを実行できます。 詳しくは、「[スナップショットが適用される前および後のスクリプトの実行](execute-scripts-before-and-after-the-snapshot-is-applied.md)」をご覧ください。  
  
-   ファイル転送プロトコル (FTP) を使用してスナップショット ファイルを転送できます。 詳細については、「[FTP によるスナップショットの転送](transfer-snapshots-through-ftp.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スナップショットを使用したサブスクリプションの初期化](initialize-a-subscription-with-a-snapshot.md)  
  
  
