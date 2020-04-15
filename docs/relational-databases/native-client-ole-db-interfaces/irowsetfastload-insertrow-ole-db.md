---
title: IRowsetFastLoad::InsertRow (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IRowsetFastLoad::InsertRow (OLE DB)
apitype: COM
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c178f2e948e27b964b04f62508ec35038b204576
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307278"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  一括コピー行セットに行を追加します。 サンプルについては、「[IRowsetFastLoad を使用したデータの一括コピー (OLE DB)](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)」と「[IROWSETFASTLOAD と ISEQUENTIALSTREAM を使用した SQL SERVER への BLOB データの送信 (OLE DB)](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)」を参照してください。  
  
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
 データ値を保持するコンシューマー所有のメモリへのポインターを指定します。 詳細については、「[DBBINDING 構造体](https://go.microsoft.com/fwlink/?LinkId=65955)」を参照してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。 すべての列のバインド状態値は、DBSTATUS_S_OK または DBSTATUS_S_NULL です。  
  
 E_FAIL  
 エラーが発生しました。 エラー情報は、行セットのエラー インターフェイスから参照できます。  
  
 E_INVALIDARG  
 *pData* 引数に NULL ポインターが設定されました。  
  
 E_OUTOFMEMORY  
 SQLNCLI11 では、要求を完了するのに必要なメモリを割り当てることができませんでした。  
  
 E_UNEXPECTED  
 既に [IRowsetFastLoad::Commit](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md) メソッドによって無効になっている一括コピー行セットに対して呼び出されました。  
  
 DB_E_BADACCESSORHANDLE   
 コンシューマーが指定した *hAccessor* 引数が無効でした。  
  
 DB_E_BADACCESSORTYPE   
 指定されたアクセサーが行アクセサーではなかったか、コンシューマー所有のメモリが指定されませんでした。  
  
## <a name="remarks"></a>解説  
 コンシューマー データを列の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型に変換するときにエラーが発生すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダからE_FAILが返されます。 **InsertRow** メソッドを使用するか、**Commit** メソッドのみを使用して、データを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に転送できます。 **InsertRow** メソッドを使用する場合、コンシューマー アプリケーションは、データ型変換エラーの通知を受け取るまで、誤ったデータを使用してこのメソッドを何回も呼び出す可能性があります。 **Commit** メソッドでは、すべてのデータがコンシューマーにより正しく指定されたことが保証されるので、コンシューマーは適切に **Commit** を使用することで、必要に応じてデータを検証できます。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダーの一括コピー行セットは書き込み専用です。 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダは、行セットのコンシューマ クエリを許可するメソッドを公開しません。 処理を終了する場合、コンシューマーは **Commit** メソッドを呼び出さずに、[IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) インターフェイスの参照を解放できます。 コンシューマーが行セットに挿入した行にアクセスして値を変更する機能や、そのような行を行セットから個別に削除する機能はありません。  
  
 一括コピーされる行は、サーバー上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用に形式が設定されます。 行の形式は、ANSI_PADDING など、接続やセッションに設定されたオプションの影響を受けます。 このオプションは、ネイティブ クライアント OLE DB プロバイダ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を介して行われた接続に対して、既定でオンに設定されます。  
  
## <a name="see-also"></a>参照  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
