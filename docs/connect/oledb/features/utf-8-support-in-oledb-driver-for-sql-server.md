---
title: OLE DB Driver for SQL Server の UTF-8 のサポート | Microsoft Docs
description: OLE DB Driver for SQL Server の UTF-8 のサポート
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: v-kaywon
ms.author: v-kaywon
ms.openlocfilehash: f410ddf4e3843936da6f93f488f379feea863e59
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744856"
---
# <a name="utf-8-support-in-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server の UTF-8 のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Microsoft OLE DB Driver for SQL Server (バージョン 18.2.1) は、utf-8 サーバー エンコードのサポートを追加します。 SQL Server の utf-8 サポートについてを参照してください。
- [照合順序と Unicode のサポート](../../../relational-databases/collations/collation-and-unicode-support.md)
- [UTF-8 のサポート (CTP 2.2)](../../../sql-server/what-s-new-in-sql-server-ver15.md#utf-8-support-ctp-22)

## <a name="data-insertion-into-a-utf-8-encoded-char-or-varchar-column"></a>エンコードされた CHAR または varchar 型の列を utf-8 へのデータの挿入
配列を使用して、バッファーが説明されている挿入のため、入力パラメーターのバッファーを作成するときに[DBBINDING 構造体](https://go.microsoft.com/fwlink/?linkid=2071182)します。 各 DBBINDING 構造体は、コンシューマーのバッファーに 1 つのパラメーターの関連付けを長さとデータ値の型などの情報が含まれています。 CHAR、型の入力パラメーター バッファー、 *wType* DBTYPE_STR の DBBINDING 構造体を設定する必要があります。 WCHAR、型の入力パラメーター バッファー、 *wType* DBTYPE_WSTR の DBBINDING 構造体を設定する必要があります。

パラメーターを持つコマンドを実行するときに、ドライバーは、パラメーターのデータ型情報を作成します。 入力バッファーの種類と、パラメーターのデータ型と一致している場合、ドライバーの変換は行われません。 それ以外の場合、ドライバーは、パラメーターのデータ型に入力パラメーターのバッファーを変換します。 パラメーターのデータ型が明示的に設定できます、ユーザーが呼び出すことによって[icommandwithparameters::setparameterinfo](https://go.microsoft.com/fwlink/?linkid=2071577)します。 情報が指定されていない場合、ドライバーは、(a) を取得する列のメタデータ サーバーから、ステートメントが準備されたときに、または (b) の入力パラメーターのデータ型から既定の変換を試みるによってパラメーターのデータ型情報を派生します。

入力パラメーターのバッファーは、入力バッファーのデータ型とパラメーターのデータ型に応じて、サーバーまたはドライバーによって、サーバーの列の照合順序に変換可能性があります。 変換中に、クライアントのコード ページまたはデータベースの照合順序コード ページは、入力バッファー内のすべての文字を表現できない場合に、データ損失が発生する可能性があります。 次の表では utf-8 にデータを挿入する列を有効にすると、変換プロセスについて説明します。

|バッファーのデータ型|パラメーター データ型|変換|ユーザーの予防措置|
|---             |---                |---       |---            |
|DBTYPE_STR|DBTYPE_STR|クライアント コード ページからデータベースの照合順序コード ページへのサーバーの変換サーバーの変換は、データベースの照合順序コード ページから列の照合順序コード ページ。|クライアントのコード ページとデータベースの照合順序コード ページが、入力データのすべての文字を表すことを確認します。 たとえば、ポーランド語の文字を挿入するには、クライアントのコード ページを 1250 (ANSI 中央ヨーロッパ言語) に設定することが、データベースの照合順序は照合順序指定子 (たとえば、Polish_100_CI_AS_SC) としてポーランド語を使用したり、utf-8 を有効にします。|
|DBTYPE_STR|DBTYPE_WSTR|クライアント コード ページから utf-16 エンコードへのドライバーの変換utf-16 エンコード列の照合順序コード ページからサーバーの変換。|クライアントのコード ページは、入力データ内のすべての文字を表すことができますを確認します。 たとえば、ポーランド語の文字を挿入するには、クライアントのコード ページを 1250 (ANSI 中央ヨーロッパ) に設定でした。|
|DBTYPE_WSTR|DBTYPE_STR|データベースの照合順序コード ページの utf-16 エンコーディングからドライバーの変換サーバーの変換は、データベースの照合順序コード ページから列の照合順序コード ページ。|データベースの照合順序コード ページは、入力データ内のすべての文字を表すことができますを確認します。 たとえば、ポーランド語の文字を挿入するデータベースの照合順序コード ページでしたポーランド語を使用して、照合順序指定子 (たとえば、Polish_100_CI_AS_SC) としてでも utf-8 で有効になっています。|
|DBTYPE_WSTR|DBTYPE_WSTR|サーバーの変換は、utf-16 から列の照合順序コード ページ。|[なし] :|

## <a name="data-retrieval-from-a-utf-8-encoded-char-or-varchar-column"></a>エンコードされた CHAR または varchar 型の列を utf-8 からデータの取得
配列を使用して、バッファーが説明されている取得したデータを格納するバッファーを作成するときに[DBBINDING 構造体](https://go.microsoft.com/fwlink/?linkid=2071182)します。 各 DBBINDING 構造体は、取得した行の 1 つの列を関連付けます。 Char 型として列のデータを取得する設定、 *wType* DBTYPE_STR、DBBINDING 構造体の。 WCHAR として列のデータを取得するには、設定、 *wType* DBTYPE_WSTR に DBBINDING 構造体の。

結果バッファー型インジケーター DBTYPE_STR には、ドライバーは、utf-8 でエンコードされたデータをクライアントのエンコーディングに変換します。 ユーザーは、クライアントのエンコーディングを表現できますデータ utf-8 列では、それ以外の場合、データの損失が発生することを確認してください。

結果バッファー型インジケーター DBTYPE_WSTR は、ドライバーは、utf-8 でエンコードされたデータを utf-16 エンコードに変換します。
  
## <a name="see-also"></a>参照  
[OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md) 

[OLE DB Driver for SQL Server の UTF-16 のサポート](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)    
  
  
