---
title: "ログ ファイル領域使用量を最小限に抑える |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- log file space in RDS [ADO]
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ae88338987beece602691060d79ec44bad93309e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="minimizing-log-file-space-usage"></a>ログ ファイル領域使用量を最小限に抑える
ログ ファイルがすぐにいっぱい (したがって、サーバーを停止する) が SQL Server データベースでのアクティビティの量が多い場合。 ログ ファイルを設定することができます**チェックポイントに Truncate**データベースのログ ファイルの有効期間を大幅に拡張します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>Microsoft SQL Server 6.5 のチェックポイントの切り捨てを有効にするには  
  
1.  Microsoft SQL Server Enterprise Manager を開始、サーバーのツリーをオープンし、データベース デバイス ツリーを開きます。  
  
2.  この機能を有効にするデータベースの名前をダブルクリックします。  
  
3.  **データベース**] タブで [ **Truncate**です。  
  
4.  **オプション** タブで、**チェックポイントのログを切り捨てる**、順にクリック**OK**です。  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>Microsoft SQL Server 7.0 でのチェックポイントの切り捨てを有効にするには  
  
1.  Microsoft SQL Server Enterprise Manager を開始、サーバーのツリーをオープンし、データベース ツリーを開きます。  
  
2.  この機能が有効になり、データベースの名前を右クリックして**プロパティ**です。  
  
3.  **オプション** タブで、**チェックポイントのログを切り捨てる**、順にクリック**OK**です。  
  
 詳細については、**チェックポイントに Truncate**機能、Microsoft SQL Server のマニュアルを参照してください。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)



