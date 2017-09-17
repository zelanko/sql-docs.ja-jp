---
title: "Open メソッド (ADO レコード) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c7e7f1c5e35ced700818954056b380a44c75570c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="open-method-ado-record"></a>Open メソッド (ADO レコード)
既存を開く[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクト、またはによって表される新しい項目の作成、**レコード**ファイルやディレクトリなどです。  
  
## <a name="syntax"></a>構文  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 省略可。 A**バリアント**これで表されるエンティティの URL を表すことがあります**レコード**オブジェクト、**コマンド**、開いている[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)または別**レコード**オブジェクト、SQL SELECT ステートメントまたはテーブル名を表す文字列。  
  
 *ActiveConnection*  
 省略可。 A**バリアント**を表す接続文字列または開いている[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
 *モード*  
 省略可。 A [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) 、結果のアクセス モードを指定する値**レコード**オブジェクト。 既定値は**adModeUnknown**です。  
  
 *CreateOptions*  
 省略可。 A [RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)既存のファイルまたはディレクトリを開くか、新しいファイルまたはディレクトリを作成する必要がありますかを示す値。 既定値は**adFailIfNotExists**です。 かどうかは、既定値に設定、アクセス モードから取得、[モード](../../../ado/reference/ado-api/mode-property-ado.md)プロパティです。 このパラメーターは無視されるときに、*ソース*パラメーターに URL が含まれていません。  
  
 *および*  
 省略可。 A [RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)開くのためのオプションを指定する値、**レコード**です。 既定値は**adOpenRecordUnspecified**です。 これらの値を組み合わせることができます。  
  
 *UserName*  
 省略可。 A**文字列**、必要な場合へのアクセスを許可するユーザー ID を表す値*ソース*です。  
  
 *Password*  
 省略可。 A**文字列**、必要な場合、以下のことを確認するためのパスワードを表す値*UserName*です。  
  
## <a name="remarks"></a>解説  
 *ソース*可能性があります。  
  
-   URL です。 URL のプロトコルが http の場合は、既定では、インターネット プロバイダーが呼び出されます。 かどうか、url には、実行可能ファイルのスクリプトを含むノード (など、します。ASP ページの場合)、**レコード**実行の代わりに、ソースを格納している内容は、既定でが開きます。 使用して、*オプション*引数この動作を変更します。  
  
-   A**レコード**オブジェクト。 A**レコード**別のオブジェクトが開かれた**レコード**元を複製**レコード**オブジェクト。  
  
-   A**コマンド**オブジェクト。 開かれている**レコード**オブジェクトが実行することによって返される 1 つの行を表す、**コマンド**です。 結果は、1 行以上を含める場合は、レコードの最初の行の内容を配置しているしにエラーが追加される可能性があります、**エラー**コレクション。  
  
-   SQL SELECT ステートメント。 開かれている**レコード**オブジェクトは、文字列の内容を実行することによって返される 1 つの行を表します。 結果は、1 行以上を含める場合は、レコードの最初の行の内容を配置しているしにエラーが追加される可能性があります、**エラー**コレクション。  
  
-   テーブル名です。  
  
 場合、**レコード**オブジェクトは、URL でアクセスできませんエンティティを表します (たとえば、行の、**レコード セット**データベースから派生)、両方の値、 [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)。プロパティとでアクセスされるフィールド、 **adRecordURL**定数が null です。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Open メソッド (ADO 接続)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema メソッド](../../../ado/reference/ado-api/openschema-method.md)
