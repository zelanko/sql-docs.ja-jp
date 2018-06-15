---
title: OpenSchema メソッド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::OpenSchema
- Connection15::raw_OpenSchema
helpviewer_keywords:
- OpenSchema method [ADO]
ms.assetid: 850cf3ce-f18f-4e7c-8597-96c1dc504866
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 780e708d5e852601333fb319291e1e9db9450c39
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280531"
---
# <a name="openschema-method"></a>OpenSchema メソッド
プロバイダーからデータベース スキーマ情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set recordset = connection.OpenSchema(QueryType, Criteria, SchemaID)  
```  
  
## <a name="return-value"></a>戻り値  
 返します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)スキーマ情報を含むオブジェクト。 **Recordset**は読み取り専用、静的カーソルとして開かれます。 *QueryType*に表示される列が、 **Recordset**です。  
  
#### <a name="parameters"></a>パラメーター  
 *QueryType*  
 どの[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)スキーマ クエリを実行の種類を表す値です。  
  
 *条件*  
 任意。 各クエリの制約の配列*QueryType*オプションに記載されている[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)です。  
  
 *SchemaID*  
 OLE DB 仕様で定義されていないプロバイダー スキーマのクエリの GUID です。 このパラメーターは必要な場合*QueryType*に設定されている**adSchemaProviderSpecific**です。 それ以外の場合は使用されません。  
  
## <a name="remarks"></a>コメント  
 **OpenSchema**メソッドを返しますが、テーブル内の列、データ ソース内のテーブルなど、データ ソースに関する情報とデータ型はサポートされています。  
  
 *QueryType*引数が列 (スキーマ) が返されるを示す GUID です。 OLE DB 仕様には、スキーマの完全な一覧があります。  
  
 *条件*引数は、スキーマのクエリの結果を制限します。 *条件*対応する結果内の制約の列と呼ばれる、列のサブセットで行う必要のある値の配列を指定**Recordset**です。  
  
 定数**adSchemaProviderSpecific**の使用、 *QueryType*引数プロバイダーは、外の独自の非標準スキーマ クエリを定義している場合前の表にします。 この定数を使用すると、 *SchemaID*を実行するスキーマのクエリの GUID を渡す引数が必要です。 場合*QueryType*に設定されている**adSchemaProviderSpecific**が*SchemaID*が提供されていない場合、エラーが発生します。  
  
 プロバイダーは、OLE DB 標準スキーマのすべてのクエリをサポートする必要はありません。 具体的には、のみ**adSchemaTables**、 **adSchemaColumns**、および**adSchemaProviderTypes**は OLE DB 仕様で必要です。 ただし、プロバイダーは、サポートする必要はありません、*条件*制約は、これらのスキーマ クエリ以前に一覧表示します。  
  
> [!NOTE]
>  **リモートのデータ サービスの使用法**、 **OpenSchema**メソッドがクライアント側で利用できない[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
> [!NOTE]
>  Visual basic での 4 バイト符号なし整数 (DBTYPE UI4) である列、 **Recordset**から返される、 **OpenSchema**メソッドを**接続**オブジェクトことはできませんその他の変数と比較されます。 OLE DB データ型の詳細については、次を参照してください。 [OLE DB (OLE DB) でのデータ型](http://msdn.microsoft.com/en-us/6039292f-74e0-49b2-b133-17bc117ebf6a)と[付録 a: データ型](http://msdn.microsoft.com/en-us/e3a0533a-2196-4eb0-a31e-92fe9556ada6)Microsoft OLE DB プログラマーズ リファレンスです。  
  
> [!NOTE]
>  **Visual C と C++ ユーザー**クライアント側のカーソルを使用していない場合は、MDAC 2.7、MDAC 2.8、および Windows Data Access Components (Windows DAC) 6.0 では、MDAC で使用される型の中に種類 VT_R8 のバリアント型を返します ADO 内の列のスキーマの"ORDINAL_POSITION"を取得します。2.6 はでした VT_I4 です。 MDAC 2.6 のバリアント型の唯一の外観に書かれたプログラムは、VT_I4 にすべての序数変更しなくても、MDAC 2.7、MDAC 2.8、および Windows DAC 6.0 で実行する場合に 0 を得られる型の返されます。 OLE DB を返すデータ型が、DBTYPE_UI4 であるために、この変更が行われ、符号付きの VT_I4 型がないが発生していると、原因となり、データが失われる可能性のある切り捨てることがなく使用可能なすべての値を格納する十分な空き領域。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [OpenSchema メソッドの例 (VB)](../../../ado/reference/ado-api/openschema-method-example-vb.md)   
 [OpenSchema メソッドの例 (vc++)](../../../ado/reference/ado-api/openschema-method-example-vc.md)   
 [Open メソッド (ADO 接続)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open メソッド (ADO レコード)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)
