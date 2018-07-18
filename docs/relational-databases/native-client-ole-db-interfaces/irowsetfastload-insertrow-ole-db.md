---
title: Irowsetfastload::insertrow (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRowsetFastLoad::InsertRow (OLE DB)
apitype: COM
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 43644b4e99efe1d6eedbe8d7fd552c0b8a543a38
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413080"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  一括コピー行セットに行を追加します。 サンプルについては、次を参照してください。[一括コピー データを使用して IRowsetFastLoad &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)と[BLOB データを SQL SERVER を使用して IROWSETFASTLOAD と ISEQUENTIALSTREAM を送信&#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)します。  
  
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
 データ値を保持するコンシューマー所有のメモリへのポインターを指定します。 詳細については、次を参照してください。 [DBBINDING 構造体](http://go.microsoft.com/fwlink/?LinkId=65955)します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。 すべての列のバインド状態値は、DBSTATUS_S_OK または DBSTATUS_S_NULL です。  
  
 E_FAIL  
 エラーが発生しました。 エラー情報は、行セットのエラー インターフェイスから参照できます。  
  
 E_INVALIDARG  
 *PData*引数が NULL ポインターに設定されました。  
  
 E_OUTOFMEMORY  
 SQLNCLI11 では、要求を完了するのに必要なメモリを割り当てることができませんでした。  
  
 E_UNEXPECTED  
 によって以前に無効にする一括コピー行セットに対してメソッドが呼び出された、 [irowsetfastload::commit](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md)メソッド。  
  
 DB_E_BADACCESSORHANDLE   
 *HAccessor*コンシューマーによって指定された引数が無効です。  
  
 DB_E_BADACCESSORTYPE   
 指定されたアクセサーが行アクセサーではなかったか、コンシューマー所有のメモリが指定されませんでした。  
  
## <a name="remarks"></a>コメント  
 コンシューマーのデータを変換中にエラー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列のデータ型と、E_FAIL からの戻り値、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー。 データを送信できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いずれかで**InsertRow**メソッドでのみ、または**コミット**メソッド。 コンシューマー アプリケーションが呼び出すことができます、 **InsertRow**メソッド、データ型変換エラーが存在するという通知を受け取るまで、誤ったデータを何度もします。 **コミット**メソッドにより、すべてのデータが正しく指定されているコンシューマーが、コンシューマーが使用できる、**コミット**メソッド適切に必要なデータを検証します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの一括コピー行セットは書き込み専用です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー行セットのコンシューマー クエリを許可するメソッドを公開しません。 処理を終了するコンシューマーは、上の参照を解放できます、 [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)呼び出さずにインターフェイス、**コミット**メソッド。 コンシューマーが行セットに挿入した行にアクセスして値を変更する機能や、そのような行を行セットから個別に削除する機能はありません。  
  
 一括コピーされる行は、サーバー上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用に形式が設定されます。 行の形式は、ANSI_PADDING など、接続やセッションに設定されたオプションの影響を受けます。 このオプションはを介して確立された接続の既定の設定、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー。  
  
## <a name="see-also"></a>参照  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
