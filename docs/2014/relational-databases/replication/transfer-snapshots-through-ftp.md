---
title: FTP によるスナップショットの転送 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 55c30791-cd2a-420b-8ba7-5700e005cb45
caps.latest.revision: 39
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a634b0cf961d922ea3169f5c44aa7c87f3ec42fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178411"
---
# <a name="transfer-snapshots-through-ftp"></a>FTP によるスナップショットの転送
  既定では、スナップショットは、UNC (Universal Naming Convention) 共有として定義されたフォルダーに格納されます。 レプリケーションでは、UNC 共有ではなく、FTP (File Transfer Protocol) 共有を指定することもできます。 FTP を使用するには、FTP サーバーを構成してから、FTP を使用するためのパブリケーションと 1 つ以上のサブスクリプションを構成する必要があります。 FTP サーバーの構成方法の詳細については、インターネット インフォメーション サービス (IIS) のドキュメントを参照してください。 パブリケーションに対して FTP 情報を指定すると、そのパブリケーションに対するサブスクリプションでは、既定で FTP を使用します。 IIS が動作しているコンピューターがファイアウォールによってディストリビューターから分離されている場合、FTP は Web 同期との組み合わせでのみ使用されます。 この場合、FTP を使用してディストリビューター、および IIS を実行中のコンピューターからスナップショットを転送できます (スナップショットは常に HTTPS を使用してサブスクライバーに転送されます)。  
  
> [!IMPORTANT]  
>  FTP 共有では、FTP パスワードを格納する必要があり、このパスワードがプレーン テキストでサブスクライバー (Web 同期が使用されている場合は、IIS が動作しているコンピューター) から FTP サーバーに送信されるため、FTP 共有ではなく [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証と UNC 共有を使用することをお勧めします。 また、1 つのアカウントがスナップショット共有へのアクセスを制御するため、フィルター選択されたマージ パブリケーションへのサブスクライバーだけに、スナップショット ファイルのデータ パーティションからスナップショット ファイルへのアクセス権が与えられていることを確認することはできません。  
  
 FTP でスナップショットを配信するには、「 [Deliver a Snapshot Through FTP](publish/deliver-a-snapshot-through-ftp.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マージ レプリケーションの Web 同期](web-synchronization-for-merge-replication.md)   
 [Initialize a Subscription with a Snapshot (スナップショットを使用したサブスクリプションの初期化)](initialize-a-subscription-with-a-snapshot.md)   
 [スナップショット オプション](snapshot-options.md)  
  
  