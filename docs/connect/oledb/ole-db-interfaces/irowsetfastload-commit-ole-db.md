---
title: Irowsetfastload::commit (OLE DB) |Microsoft Docs
description: IRowsetFastLoad::Commit (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IRowsetFastLoad::Commit (OLE DB)
apitype: COM
helpviewer_keywords:
- Commit method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 6f4f4ff01e34dff092f87b3dc1f972a5ab31ca6c
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51031429"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  挿入される行のバッチの終わりをマークし、挿入された行を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のテーブルに書き込みます。 サンプルについては、次を参照してください。[一括コピー データを使用して IRowsetFastLoad &#40;OLE DB&#41; ](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)と[BLOB データを SQL SERVER を使用して IROWSETFASTLOAD と ISEQUENTIALSTREAM を送信&#40;OLE DB&#41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT Commit(  
      BOOL fDone);  
```  
  
## <a name="arguments"></a>引数  
 *fDone*[in]  
 FALSE の場合、行セットは有効なまま保持され、コンシューマーはこの行セットを使用してさらに行を挿入できます。 TRUE の場合、行セットは無効になり、コンシューマーはこれ以上行を挿入できません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功し、挿入されたすべてのデータが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルに書き込まれました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。 特定のエラー テキストのエラー情報をプロバイダーから取得してください。  
  
 E_UNEXPECTED  
 既に **IRowsetFastLoad::Commit** メソッドによって無効になっている一括コピー行セットに対して呼び出されました。  
  
## <a name="remarks"></a>Remarks  
 OLE DB Driver for SQL Server 一括コピー行セットは、遅延更新モードの行セットとして動作します。 ユーザーが行セットを使用して行データを挿入すると、挿入された行は、**IRowsetUpdate** をサポートする行セットでの保留中の挿入と同様の形式で扱われます。  
  
 コンシューマーは、**IRowsetUpdate::Update** メソッドを使用して保留中の行を SQL Server のインスタンスに送信するのと同様に、一括コピー行セットに対して **Commit** メソッドを呼び出して、挿入された行を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルに書き込む必要があります。  
  
 コンシューマーが **Commit** メソッドを呼び出さないで一括コピー行セットの参照を解放すると、挿入されてもそれ以前に書き込まれていない行はすべて失われます。  
  
 コンシューマーは、*fDone* 引数を FALSE に設定して **Commit** メソッドを呼び出すことにより、挿入される行をバッチ処理できます。 *fDone* を TRUE に設定すると、その行セットは無効になります。 無効な一括コピー行セットでは、**ISupportErrorInfo** インターフェイスと **IRowsetFastLoad::Release** メソッドのみがサポートされます。  
  
## <a name="see-also"></a>参照  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
