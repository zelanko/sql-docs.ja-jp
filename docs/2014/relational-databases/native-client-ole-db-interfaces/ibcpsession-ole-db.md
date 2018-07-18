---
title: IBCPSession (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d1b8b0ed771996ccd6045c28199dbe0c02a37a3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430061"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
  **IBCPSession**インターフェイスのサポートを公開する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ファイルベースの一括コピー操作。 **IBCPSession**でインターフェイスが公開されている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セッションとして同じレベルでの Native Client OLE DB プロバイダー。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、データ ソース オブジェクトは、セッション オブジェクトのファクトリと、一括コピー操作は、接続プロパティ SSPROP_ENABLEBULKCOPY で指定されます。 また、SSPROP_ENABLEFASTLOAD プロパティは true に設定する必要があります。  
  
 呼び出す、 **idbcreatesession::createsession**メソッドは、その結果、作成、 **BulkCopySession**オブジェクト。 を介して公開されるすべてのファイル ベースの一括コピー メソッド、 **IBCPSession**オブジェクトは、これとほぼ同じシグネチャを持つ呼び出し可能**IBCPSession**オブジェクトの**IBCPSession**インターフェイス。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー経由のメモリベースの一括コピー操作をサポートしている、 [IRowsetFastLoad](irowsetfastload-ole-db.md)インターフェイス。  
  
 使用しての詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの一括コピー操作を参照してください[一括コピー操作を実行する](../native-client/features/performing-bulk-copy-operations.md)します。  
  
 使用する方法を示すサンプルについては、 **IBCPSession**インターフェイスは、「 [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|方法|説明|  
|------------|-----------------|  
|[Ibcpsession::bcpcolfmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md)|プログラム変数と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のバインドを作成します。|  
|[Ibcpsession::bcpcolumns &#40;OLE DB&#41;](ibcpsession-bcpcolumns-ole-db.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列にバインドされるフィールド数を設定します。|  
|[Ibcpsession::bcpcontrol &#40;OLE DB&#41;](ibcpsession-bcpcontrol-ole-db.md)|一括コピー操作のオプションを設定します。|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信される残りの行をコミットします。|  
|[:Bcpexec &#40;OLE DB&#41;](ibcpsession-bcpexec-ole-db.md)|一括コピー操作を実行します。|  
|[Ibcpsession::bcpinit &#40;OLE DB&#41;](ibcpsession-bcpinit-ole-db.md)|一括コピー構造を初期化し、エラー チェックを実行して、データ ファイルとフォーマット ファイルの名前が正しいことを確認します。その後、それらのファイルを開きます。|  
|[Ibcpsession::bcpreadfmt &#40;OLE DB&#41;](ibcpsession-bcpreadfmt-ole-db.md)|フォーマット ファイルから列ごとにフォーマット情報を読み取ります。|  
|[Ibcpsession::bcpwritefmt &#40;OLE DB&#41;](ibcpsession-bcpwritefmt-ole-db.md)|フォーマット ファイルに列ごとのフォーマット情報を書き込みます。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
