---
title: IRowsetFastLoad (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35cee52e9a85989123bcb10d998d37ce86a28601
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63209814"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
  インターフェイス`IRowsetFastLoad`は、メモリベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の一括コピー操作のサポートを公開します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーコンシューマーは、インターフェイスを使用して、既存[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のテーブルにデータを迅速に追加します。  
  
 セッションで SSPROP_ENABLEFASTLOAD を VARIANT_TRUE に設定した場合、その後にそのセッションから返される行セットのデータを読み取ることはできません。 SSPROP_ENABLEFASTLOAD が VARIANT_TRUE に設定されている場合、そのセッションで作成される行セットはすべて IRowsetFastLoad 型になります。 IRowsetFastLoad の行セットは行セットのフェッチをサポートしていないため、これらの行セットのデータを読み取ることはできません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|方法|[説明]|  
|------------|-----------------|  
|[IRowsetFastLoad:: Commit &#40;OLE DB&#41;](irowsetfastload-commit-ole-db.md)|挿入される行のバッチの終わりをマークし、挿入された行を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルに書き込みます。|  
|[IRowsetFastLoad:: InsertRow &#40;OLE DB&#41;](irowsetfastload-insertrow-ole-db.md)|一括コピー行セットに行を追加します。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [IRowsetFastLoad &#40;OLE DB を使用した一括データコピー&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [IROWSETFASTLOAD と ISEQUENTIALSTREAM &#40;OLE DB を使用して SQL SERVER に BLOB データを送信する&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
