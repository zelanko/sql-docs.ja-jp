---
title: IBCPSession (OLE DB) |Microsoft ドキュメント
description: IBCPSession インターフェイス (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IBCPSession interface
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: fa5b620c5f8333ff54a046055e90867cedbfa87b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **IBCPSession**インターフェイスのサポートが公開[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ファイルベースの一括コピー操作します。 **IBCPSession**セッションと同じレベルの下で OLE DB Driver for SQL Server インターフェイスを公開されます。 OLE DB Driver for SQL Server、データ ソース オブジェクトは Session オブジェクトのファクトリで一括コピー操作は、接続プロパティ SSPROP_ENABLEBULKCOPY で指定します。 また、SSPROP_ENABLEFASTLOAD プロパティは true に設定する必要があります。  
  
 呼び出す、 **idbcreatesession::createsession**メソッドは、その結果の作成、 **BulkCopySession**オブジェクト。 を通じて公開されるすべてのファイル ベースの一括コピー メソッド、 **IBCPSession**オブジェクトがこれによく似たシグネチャを持つ呼び出し可能な**IBCPSession**オブジェクトの**IBCPSession**インターフェイスです。  
  
> [!NOTE]  
>  SQL Server の OLE DB Driver 経由のメモリベースの一括コピー操作をサポートしています、 [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)インターフェイスです。  
  
 SQL Server の OLE DB Driver を使用して一括コピー操作の詳細については、次を参照してください。[一括コピー操作の実行](../../oledb/features/performing-bulk-copy-operations.md)です。  
  
 使用する方法を示すサンプルについては、 **IBCPSession**インターフェイスを参照してください[IBCPSession::BCPDone &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|方法|Description|  
|------------|-----------------|  
|[Ibcpsession::bcpcolfmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|プログラム変数と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 列のバインドを作成します。|  
|[Ibcpsession::bcpcolumns &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブル内の列にバインドされるフィールド数を設定します。|  
|[Ibcpsession::bcpcontrol &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|一括コピー操作のオプションを設定します。|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信される残りの行をコミットします。|  
|[:Bcpexec &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|一括コピー操作を実行します。|  
|[Ibcpsession::bcpinit &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|一括コピー構造を初期化し、エラー チェックを実行して、データ ファイルとフォーマット ファイルの名前が正しいことを確認します。その後、それらのファイルを開きます。|  
|[Ibcpsession::bcpreadfmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|フォーマット ファイルから列ごとにフォーマット情報を読み取ります。|  
|[Ibcpsession::bcpwritefmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|フォーマット ファイルに列ごとのフォーマット情報を書き込みます。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス (&) #40";"OLE DB"&"#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)  
  
  
