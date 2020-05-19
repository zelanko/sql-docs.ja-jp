---
title: IBCPSession (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 10165ed57c12b06fc1317bb440dd1635849582f6
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82695246"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
  **IBCPSession** インターフェイスでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のファイルベースの一括コピー操作のサポートが公開されます。 **Ibcpsession**インターフェイスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブクライアント OLE DB プロバイダーのセッションと同じレベルで公開されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、データソースオブジェクトはセッションオブジェクトのファクトリであり、SSPROP_ENABLEBULKCOPY の接続プロパティには一括コピー操作が指定されています。 また、SSPROP_ENABLEFASTLOAD プロパティは true に設定する必要があります。  
  
 **IDBCreateSession::CreateSession** メソッドを呼び出すと、**BulkCopySession** オブジェクトが作成されます。 その後、作成された **IBCPSession** オブジェクトの **IBCPSession** インターフェイスとほぼ同じシグネチャを使用して、**IBCPSession** オブジェクト経由で公開されるファイルベースのすべての一括コピー メソッドを呼び出せるようになります。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 [IRowsetFastLoad](irowsetfastload-ole-db.md)インターフェイスを使用して、メモリベースの一括コピー操作をサポートします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブクライアント OLE DB プロバイダーを使用した一括コピー操作の詳細については、「[一括コピー操作の実行](../native-client/features/performing-bulk-copy-operations.md)」を参照してください。  
  
 **IBCPSession** インターフェイスの使用方法を示したサンプルについては、「[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|メソッド|説明|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md)|プログラム変数と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のバインドを作成します。|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](ibcpsession-bcpcolumns-ole-db.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列にバインドされるフィールド数を設定します。|  
|[IBCPSession::BCPControl &#40;OLE DB&#41;](ibcpsession-bcpcontrol-ole-db.md)|一括コピー操作のオプションを設定します。|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信される残りの行をコミットします。|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](ibcpsession-bcpexec-ole-db.md)|一括コピー操作を実行します。|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](ibcpsession-bcpinit-ole-db.md)|一括コピー構造を初期化し、エラー チェックを実行して、データ ファイルとフォーマット ファイルの名前が正しいことを確認します。その後、それらのファイルを開きます。|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](ibcpsession-bcpreadfmt-ole-db.md)|フォーマット ファイルから列ごとにフォーマット情報を読み取ります。|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](ibcpsession-bcpwritefmt-ole-db.md)|フォーマット ファイルに列ごとのフォーマット情報を書き込みます。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
