---
title: Irowsetfastload::insertrow (OLE DB) |Microsoft ドキュメント
description: IRowsetFastLoad::InsertRow (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRowsetFastLoad::InsertRow (OLE DB)
apitype: COM
helpviewer_keywords:
- InsertRow method
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4fbf689d2e31aee6b962254c61b90c210d0a0c6d
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  一括コピー行セットに行を追加します。 サンプルについては、次を参照してください。[一括コピー データを使用して IRowsetFastLoad &#40;OLE DB&#41; ](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)と[SQL SERVER を使用して IROWSETFASTLOAD と ISEQUENTIALSTREAM に BLOB データを送信&#40;OLE DB&#41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT InsertRow(  
      HACCESSOR hAccessor,  
      void* pData);  
```  
  
## <a name="arguments"></a>引数  
 *hAccessor*[in]  
 一括コピーの行データを定義するアクセサーのハンドルを指定します。 参照されるアクセサーは行アクセサーで、データ値を保持するコンシューマー所有のメモリをバインドします。  
  
 *pData*[in]  
 データ値を保持するコンシューマー所有のメモリへのポインターを指定します。 詳細については、次を参照してください。 [DBBINDING 構造体](http://go.microsoft.com/fwlink/?LinkId=65955)です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。 すべての列のバインド状態値は、DBSTATUS_S_OK または DBSTATUS_S_NULL です。  
  
 E_FAIL  
 エラーが発生しました。 エラー情報は、行セットのエラー インターフェイスから参照できます。  
  
 E_INVALIDARG  
 *PData*引数が NULL ポインターに設定されました。  
  
 E_OUTOFMEMORY  
 MSOLEDBSQL は要求を完了するための十分なメモリを割り当てることができませんでした。  
  
 E_UNEXPECTED  
 によって以前に無効に一括コピー行セットに対してメソッドが呼び出された、 [irowsetfastload::commit](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md)メソッドです。  
  
 DB_E_BADACCESSORHANDLE   
 *HAccessor*コンシューマーによって提供される引数が無効です。  
  
 DB_E_BADACCESSORTYPE   
 指定されたアクセサーが行アクセサーではなかったか、コンシューマー所有のメモリが指定されませんでした。  
  
## <a name="remarks"></a>解説  
 コンシューマー データを変換中にエラー、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]原因列のデータ型は SQL Server の OLE DB ドライバーからの E_FAIL 戻り値。 データを送信できる[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の**InsertRow**メソッドでのみ、または**コミット**メソッドです。 コンシューマー アプリケーションが呼び出すことができます、 **InsertRow**何度も、データ型変換エラーが存在するという通知を受け取るまで、誤ったデータを持つメソッドです。 **コミット**メソッドにより、すべてのデータが正しく指定されている、コンシューマーによってコンシューマーが使用できる、**コミット**メソッド適切に必要に応じて、データを検証します。  
  
 SQL Server 一括コピー行セットの OLE DB Driver は、書き込み専用です。 SQL Server の OLE DB Driver は、行セットのコンシューマー クエリを許可するメソッドを公開ありません。 処理を終了する、コンシューマーは、上の参照を解放できます、 [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)インターフェイスを呼び出さず、**コミット**メソッドです。 コンシューマーが行セットに挿入した行にアクセスして値を変更する機能や、そのような行を行セットから個別に削除する機能はありません。  
  
 一括コピーされる行は、サーバー上で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用に形式が設定されます。 行の形式は、ANSI_PADDING など、接続やセッションに設定されたオプションの影響を受けます。 このオプションは既定では、SQL Server の OLE DB ドライバーを介して確立された接続で設定されます。  
  
## <a name="see-also"></a>参照  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
