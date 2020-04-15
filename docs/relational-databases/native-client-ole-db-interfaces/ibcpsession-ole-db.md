---
title: IBCPSession (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 653bd8aad3a10a3929b7ced76e28e4d570733ad3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307349"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **IBCPSession** インターフェイスでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のファイルベースの一括コピー操作のサポートが公開されます。 **IBCPSession**インターフェイスは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントの OLE DB プロバイダーでセッションと同じレベルで公開されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーでは、データ ソース オブジェクトは Session オブジェクトのファクトリであり、一括コピー操作は接続プロパティ SSPROP_ENABLEBULKCOPYで指定されます。 また、SSPROP_ENABLEFASTLOAD プロパティは true に設定する必要があります。  
  
 **IDBCreateSession::CreateSession** メソッドを呼び出すと、**BulkCopySession** オブジェクトが作成されます。 その後、作成された **IBCPSession** オブジェクトの **IBCPSession** インターフェイスとほぼ同じシグネチャを使用して、**IBCPSession** オブジェクト経由で公開されるファイルベースのすべての一括コピー メソッドを呼び出せるようになります。  
  
> [!NOTE]  
>  ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーは[、IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)インターフェイスを介してメモリ ベースの一括コピー操作をサポートします。  
  
 一括コピー操作にネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダを使用する方法の詳細については、「[一括コピー操作の実行](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)」を参照してください。  
  
 **IBCPSession** インターフェイスの使用方法を示したサンプルについては、「[IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|Method|説明|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|プログラム変数と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のバインドを作成します。|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列にバインドされるフィールド数を設定します。|  
|[IBCPSession::BCPControl &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|一括コピー操作のオプションを設定します。|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信される残りの行をコミットします。|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|一括コピー操作を実行します。|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|一括コピー構造を初期化し、エラー チェックを実行して、データ ファイルとフォーマット ファイルの名前が正しいことを確認します。その後、それらのファイルを開きます。|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|フォーマット ファイルから列ごとにフォーマット情報を読み取ります。|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|フォーマット ファイルに列ごとのフォーマット情報を書き込みます。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
