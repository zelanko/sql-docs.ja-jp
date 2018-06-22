---
title: Irowsetfastload::commit (OLE DB) |Microsoft ドキュメント
description: IRowsetFastLoad::Commit (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRowsetFastLoad::Commit (OLE DB)
apitype: COM
helpviewer_keywords:
- Commit method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8f4baa2339105e8dac65c29e5efc35663b7c4b8d
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689855"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  挿入される行のバッチの終わりをマークし、挿入された行を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のテーブルに書き込みます。 サンプルについては、次を参照してください。[一括コピー データを使用して IRowsetFastLoad &#40;OLE DB&#41; ](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)と[SQL SERVER を使用して IROWSETFASTLOAD と ISEQUENTIALSTREAM に BLOB データを送信&#40;OLE DB&#41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)です。  
  
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
 によって以前に無効に一括コピー行セットに対してメソッドが呼び出された、 **irowsetfastload::commit**メソッドです。  
  
## <a name="remarks"></a>コメント  
 OLE DB Driver for SQL Server 一括コピー行セットは、遅延更新モードの行セットとして動作します。 保留中の挿入、行セットをサポートするのに挿入された行が同じ方法で扱われるように、行セットから行のデータを挿入すると、 **IRowsetUpdate**です。  
  
 コンシューマーは、呼び出す必要があります、**コミット**書き込む挿入された行を一括コピー行セットのメソッド、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]と同じ方法でテーブル、 **irowsetupdate::update**メソッドを使用して、保留中の行を送信、SQL Server のインスタンス。  
  
 コンシューマーに呼び出さずに一括コピー行セットの参照を解放する場合、**コミット**メソッド、すべての挿入されたなかった書き込まれた行は失われます。  
  
 コンシューマーは、挿入された行をバッチ処理を呼び出して、**コミット**メソッドを*fDone*引数が FALSE に設定します。 ときに*fDone*が TRUE に設定すると、行セットは無効になります。 無効な一括コピー行セットのみをサポート、 **ISupportErrorInfo**インターフェイスと**irowsetfastload::release**メソッドです。  
  
## <a name="see-also"></a>参照  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
