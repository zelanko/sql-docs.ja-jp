---
title: "Excel のカスタム プロパティ | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdcc72b8-8950-47bd-88bf-5db6d48cc6bf
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62f9ea61469870e751b48dad555f5e6f68ba9833
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="excel-custom-properties"></a>Excel のカスタム プロパティ
  **変換元のカスタム プロパティ**  
  
 Excel ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、Excel ソースのカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|データベースへのアクセスに使用するモード。 値には、 **OpenRowset**、 **OpenRowset from Variable**、 **SQL Command**、および **SQL Command from Variable**があります。 既定値は **OpenRowset**です。|  
|CommandTimeOut|Integer|コマンドのタイムアウトの秒数。値 0 は、タイムアウトしないことを表します。<br /><br /> **注** : このプロパティは、 **Excel ソース エディター**では使用できませんが、 **詳細エディター**を使用して設定できます。|  
|OpenRowset|文字列|行セットを開くために使用するデータベース オブジェクトの名前。|  
|OpenRowsetVariable|文字列|行セットを開くために使用するデータベース オブジェクトの名前を格納する変数。|  
|ParameterMapping|文字列|SQL コマンド内のパラメーターから変数へのマッピング。|  
|SqlCommand|文字列|実行する SQL コマンド。|  
|SqlCommandVariable|文字列|実行する SQL コマンドを格納する変数。|  
  
 Excel ソースの出力および出力列には、カスタム プロパティがありません。  
  
 詳細については、「 [Excel ソース](../../integration-services/data-flow/excel-source.md)」を参照してください。  
  
 **変換先のカスタム プロパティ**  
  
 Excel 変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、Excel 変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (列挙)|変換先が変換先となるデータベースにアクセスする方法を指定する値。<br /><br /> このプロパティの値は、次のいずれか 1 つです。<br /><br /> **OpenRowset** (0): テーブルまたはビューの名前を指定します。<br /><br /> **OpenRowset from Variable** (1): テーブルまたはビューの名前が含まれる変数の名前を指定します。<br /><br /> **OpenRowset Using Fastload** (3): テーブルまたはビューの名前を指定します。<br /><br /> **OpenRowset Using Fastload from Variable** (4): テーブルまたはビューの名前が含まれる変数の名前を指定します。<br /><br /> **SQL Command** (2): SQL ステートメントを指定します。|  
|CommandTimeOut|Integer|SQL コマンドがタイムアウトになるまでの最大秒数。この値に **0** を指定すると、時間は無制限になります。 このプロパティの既定値は **0**です。<br /><br /> 注: このプロパティは、 **Excel 変換先エディター**では使用できませんが、 **詳細エディター**を使用して設定できます。|  
|FastLoadKeepIdentity|ブール値|データが読み込まれるときに ID 値をコピーするかどうかを指定する値。 このプロパティは、高速読み取りオプションのいずれかを使用した場合のみ使用できます。 このプロパティの既定値は **False**です。|  
|FastLoadKeepNulls|ブール値|データが読み込まれるときに NULL 値をコピーするかどうかを指定する値。 このプロパティは、高速読み取りオプションのいずれかを使用した場合のみ使用できます。 このプロパティの既定値は **False**です。|  
|FastLoadMaxInsertCommitSize|Integer|高速読み込み操作の実行中に、Excel 変換先でコミットを試行するバッチ サイズを指定する値。 既定値は **2147483647**す。 値 **0** は、すべての行が処理された後で、コミット操作が 1 回行われることを示します。|  
|FastLoadOptions|文字列|高速読み込みオプションのコレクション。 高速読み込みオプションには、テーブルのロックおよび制約のチェックが含まれています。 どちらか 1 つまたは両方を指定することも、どちらも指定しないこともできます。<br /><br /> 注: このプロパティの一部のオプションは、 **Excel 変換先エディター**では使用できませんが、 **詳細エディター**を使用して設定できます。|  
|OpenRowset|文字列|AccessMode が **OpenRowset**の場合、Excel 変換先がアクセスするテーブルまたはビューの名前。|  
|OpenRowsetVariable|文字列|AccessMode が **OpenRowset from Variable**の場合、Excel 変換先がアクセスするテーブルまたはビューの名前が含まれる変数名。|  
|SqlCommand|文字列|AccessMode が **SQL Command**の場合、Excel 変換先がデータの変換先列を指定するときに使用する、Transact-SQL ステートメント。|  
  
 Excel 変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [Excel 変換先](../../integration-services/data-flow/excel-destination.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [共通プロパティ](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
