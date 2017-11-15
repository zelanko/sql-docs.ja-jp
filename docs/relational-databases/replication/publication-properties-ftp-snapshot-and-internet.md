---
title: "[パブリケーションのプロパティ]、[FTP スナップショットとインターネット] | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.newpubwizard.pubproperties.internetsynchronization.f1
ms.assetid: 8e0198c3-5e4e-418c-9920-78ccbbfc1323
caps.latest.revision: "25"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 39e7279dafbfbcf8f1442c99597817b4f1ce3a92
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="publication-properties-ftp-snapshot-and-internet"></a>[パブリケーションのプロパティ]、[FTP スナップショットとインターネット]
  このページで以下の操作を実行できます。  
  
-   ファイル転送プロトコル (FTP) を通じてスナップショットを配信するためのプロパティを設定する。 詳細については、「[FTP によるスナップショットの転送](../../relational-databases/replication/transfer-snapshots-through-ftp.md)」を参照してください。 スナップショットの配信に FTP を使用するには、FTP サーバーを設定する必要があります。 詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のマニュアルを参照してください。  
  
    > [!NOTE]  
    >  FTP 設定を変更するには、新しいスナップショットを生成する必要があります。  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでのマージ レプリケーションに対して、Web 同期のプロパティを設定して、サブスクリプションを HTTPS (安全なハイパーテキスト転送プロトコル) 経由で同期できるようにする。 Web 同期を使用するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) サーバーを構成する必要があります。 詳細については、「 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[FTP 経由でスナップショットにアクセス]**  
 **[ファイル転送プロトコル (FTP) を使用したスナップショット ファイルのダウンロードをサブスクライバーに許可する]**を選択し、 **[FTP サーバー名]**、 **[ポート番号]**、 **[FTP ルート フォルダーからのパス]**、 **[ログイン]**、および **[パスワード]**を指定し、サブスクライバーがスナップショットの配信に FTP を使用できるようにします。  
  
 このオプションを選択すると、サブスクライバーは FTP を使用してスナップショット ファイルを取得できますが、この設定は必須ではありません。 このオプションを選択した場合、サブスクリプションの新規作成ウィザードでは、サブスクライバーがスナップショット ファイルを FTP 経由で取得する設定が既定で有効になります。 設定を変更するには、 **[サブスクリプションのプロパティ]** ダイアログ ボックスを使用します。 サブスクライバーが FTP 経由でスナップショットにアクセスするように設定する場合は、 **[パブリケーションのプロパティ]** ダイアログ ボックスの **[スナップショット]** ページで、スナップショット ファイルの場所として FTP フォルダーを指定します。 これにより、スナップショット エージェントは、新しいスナップショットが生成されたときに FTP フォルダー内のファイルを自動的に更新します。 場所を FTP フォルダーに設定していない場合は、新しいスナップショットが生成されたときにファイルを手動で更新する必要があります。 詳細については、「[FTP でのスナップショットの配信](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)」を参照してください。  
  
 **[Web 同期]**  
 マージ レプリケーションのみです。 **[Web サーバーへの接続による同期をサブスクライバーに許可する]**を選択し、マージ サブスクライバーが Web 同期を使用できるように Web サーバー アドレスを指定します。 Web サーバーは、SSL (Secure Sockets Layer) を使用する必要があります。また、Web アドレスは `https://server.domain.com/synchronize` のように完全修飾である必要があります。 詳しくは、「 [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [プル サブスクリプションのプロパティの表示または変更](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [プッシュ サブスクリプションのプロパティの表示または変更](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [初期スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
