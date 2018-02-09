---
title: "十分な TempDB 領域を確保する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TempDB space in RDS [ADO]
ms.assetid: 09130db1-6248-4234-a1e5-a9c8e1622c06
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1b25883b6e0d2b52719b4227d0fbec1abdf31eae
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="ensuring-sufficient-tempdb-space"></a>十分な TempDB 領域を確保します。
処理中にエラーが発生した場合[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)を Microsoft SQL Server 6.5 の領域の処理を必要とするオブジェクト、TempDB のサイズを大きく必要があります。 (一部のクエリ処理の一時領域が必要ですたとえば、ORDER BY 句を使用してクエリには、並べ替えが必要です。 の、 **Recordset**、いくつかの一時ディスク領域を作成する必要があります。)。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
> [!IMPORTANT]
>  ほど簡単に展開されていると、デバイスの圧縮はないため、操作を実行する前に、この手順を通してください。  
  
> [!NOTE]
>  既定の形状で SQL Server 7.0 以降、TempDB は、必要に応じて自動的に拡張に設定されます。 したがって、この手順が 7.0 より前のバージョンを実行するサーバーで必要なのみ可能性があります。  
  
### <a name="to-increase-the-tempdb-space-on-sql-server-65"></a>SQL Server 6.5 に TempDB の領域を増やす  
  
1.  Microsoft SQL Server Enterprise Manager を開始、サーバーのツリーをオープンし、データベース デバイス ツリーを開きます。  
  
2.  マスターなどを展開するに (物理) デバイスを選択し、デバイスを開くにはダブルクリック、**データベース デバイスの編集** ダイアログ ボックス。  
  
     このダイアログ ボックスでは、現在のデータベースを使用している領域の量を表示します。  
  
3.  **サイズ**ボックスで、指定したサイズ (たとえば、50 メガバイト (MB) のハード_ディスク領域) デバイスを大ききます。  
  
4.  をクリックして**今すぐ変更**を (論理) の TempDB の拡張可能領域の量を増やします。  
  
5.  サーバーで、データベースのツリーを開き、ダブルクリックして**TempDB**を開くには、**データベースの編集** ダイアログ ボックス。 **データベース**タブには、TempDB に現在割り当てられている領域の量が一覧表示されます (**データ サイズ**)。 既定では、これは 2 MB です。  
  
6.  下にある、**サイズ**グループで、**展開**です。 グラフは、各物理デバイスに、使用可能な領域と割り当てられた領域を表示します。 茶色のバーは、使用可能な領域を表します。  
  
7.  選択、**ログ デバイス**、マスターが使用可能なサイズを表示するなど、**サイズ (MB)**ボックス。  
  
8.  をクリックして**今すぐ展開**TempDB データベースにその領域を割り当てます。  
  
     **データベースの編集** ダイアログ ボックスが表示されます、新しいサイズを TempDB に割り当てられます。  
  
 このトピックに関する詳細については、Microsoft SQL Server Enterprise Manager のヘルプ ファイルを検索します「展開データベース ダイアログ ボックス」  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)


