---
title: "IBCPSession (OLE DB) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: COM
helpviewer_keywords: IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6eacf5221fe9da52891f4a198aae5076fe5b29a0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **IBCPSession**インターフェイスのサポートが公開[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ファイルベースの一括コピー操作します。 **IBCPSession**でインターフェイスが公開されている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セッションと同じレベルでの Native Client OLE DB プロバイダーです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがデータ ソース オブジェクトは Session オブジェクトのファクトリと、一括コピー操作は、接続プロパティ SSPROP_ENABLEBULKCOPY で指定します。 また、SSPROP_ENABLEFASTLOAD プロパティは true に設定する必要があります。  
  
 呼び出す、 **idbcreatesession::createsession**メソッドは、その結果の作成、 **BulkCopySession**オブジェクト。 を通じて公開されるすべてのファイル ベースの一括コピー メソッド、 **IBCPSession**オブジェクトがこれによく似たシグネチャを持つ呼び出し可能な**IBCPSession**オブジェクトの**IBCPSession**インターフェイスです。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー経由のメモリベースの一括コピー操作をサポートしている、 [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)インターフェイスです。  
  
 使用しての詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの一括コピー操作を参照してください[一括コピー操作の実行](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)です。  
  
 使用する方法を示すサンプルについては、 **IBCPSession**インターフェイスを参照してください[IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|方法|Description|  
|------------|-----------------|  
|[Ibcpsession::bcpcolfmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|プログラム変数と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のバインドを作成します。|  
|[Ibcpsession::bcpcolumns &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列にバインドされるフィールド数を設定します。|  
|[Ibcpsession::bcpcontrol &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|一括コピー操作のオプションを設定します。|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信される残りの行をコミットします。|  
|[:Bcpexec &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|一括コピー操作を実行します。|  
|[Ibcpsession::bcpinit &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|一括コピー構造を初期化し、エラー チェックを実行して、データ ファイルとフォーマット ファイルの名前が正しいことを確認します。その後、それらのファイルを開きます。|  
|[Ibcpsession::bcpreadfmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|フォーマット ファイルから列ごとにフォーマット情報を読み取ります。|  
|[Ibcpsession::bcpwritefmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|フォーマット ファイルに列ごとのフォーマット情報を書き込みます。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
