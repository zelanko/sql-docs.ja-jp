---
title: "絶対と相対 Url |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- relative URLs [ADO]
- absolute URLs [ADO]
- URLs [ADO]
ms.assetid: 6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c87fea24a0f03bbf179c74102fbb5514873f134a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="absolute-and-relative-urls"></a>絶対と相対 Url
URL では、ローカルまたはネットワーク上のコンピューターに格納されているターゲットの場所を指定します。 ファイル、ディレクトリ、HTML ページ、画像、プログラム、およびなど、ターゲットにできます*です。*  
  
 *絶対 URL*リソースを特定するために必要なすべての情報が含まれています。  
  
 A*相対 URL*開始点としては、絶対 URL を使用してリソースを検索します。 実際には、「完全 URL」、ターゲットは、絶対と相対 Url を連結することによって指定されます。  
  
 *絶対 URL* 、次の形式を使用して: *scheme://server/path/resource*  
  
 相対 URL 通常のみで構成されて、*パス*、し、必要に応じて、*リソース*が*スキーム*または*サーバー*です。 次の表は、完全な URL の形式の個々 の部分を定義します。  
  
 *スキーム*  
 指定する方法、*リソース*へのアクセスします。  
  
 *サーバー*  
 コンピューターの名前を指定場所、*リソース*が配置されています。  
  
 *パス*  
 一連の先頭のターゲットにディレクトリを指定します。 場合*リソース*は内の最後のディレクトリがターゲットを省略すると、*パス*です。  
  
 *リソース*  
 含まれる場合、*リソース*ターゲットは、通常、ファイルの名前。 ある可能性があります、*単純なファイルは、* (バイト単位) の 1 つのバイナリ ストリームを含むまたは*構造化ドキュメントは、* 1 つまたは複数の記憶域とのバイトのバイナリ ストリームを含むです。  
  
## <a name="url-scheme-registration"></a>URL スキームの登録  
 プロバイダーは、Url をサポートする場合、プロバイダーは 1 つまたは複数の URL スキームに登録されます。 登録するには、スキームを使用する Url の登録済みのプロバイダーによって自動的に起動されることを意味します。 たとえば、 *http*にスキームが登録されている、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 ADO では、"http"の付いたすべての Url を表すインターネット発行プロバイダーと共に使用する Web フォルダーまたはファイルを前提としています。 プロバイダーが登録されているスキーマの詳細については、プロバイダーのマニュアルを参照してください。  
  
## <a name="defining-context-with-a-url"></a>URL を使用してコンテキストを定義します。  
 によって表される、開いている接続の 1 つの関数、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト、その接続で表されるデータ ソースへの後続の操作を制限するはします。 つまり、接続は、後続の操作コンテキストを定義します。  
  
 Ado 2.7 以降では、絶対 URL コンテキストを定義できます。 たとえばときに、[レコード](../../../ado/reference/ado-api/record-object-ado.md)絶対 URL でオブジェクトを開く、**接続**オブジェクトは、URL で指定されたリソースを表すために暗黙的に作成します。  
  
 コンテキストを定義する絶対 URL を指定することができます、 *ActiveConnection*のパラメーター、**レコード**オブジェクト[開く](../../../ado/reference/ado-api/open-method-ado-record.md)メソッドです。 値として絶対 URL を指定することも、"URL**=**"キーワード、**接続**オブジェクト[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッド*ConnectionString*パラメーター、および[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッド*ActiveConnection*パラメーター。  
  
 開くことでコンテキストを定義することも、**レコード**または**Recordset**をこれらのオブジェクトが既にがある、暗黙的または明示的に宣言されているため、ディレクトリを表すオブジェクト**接続**コンテキストを指定するオブジェクト。  
  
## <a name="scoped-operations"></a>スコープを設定した操作  
 コンテキストもスコープを定義-は、ディレクトリとそのサブディレクトリの後続の操作に含めることができます。 **レコード**オブジェクトがディレクトリを操作するいくつかのスコープを持つメソッドとそのすべてのサブディレクトリ。 これらのメソッドを含める[つまり](../../../ado/reference/ado-api/copyrecord-method-ado.md)、[後続](../../../ado/reference/ado-api/moverecord-method-ado.md)、および[関係する](../../../ado/reference/ado-api/deleterecord-method-ado.md)です。  
  
## <a name="relative-urls-as-command-text"></a>コマンド テキストと相対 Url  
 文字列を入力して、データ ソースで実行されるコマンドを指定することができます、 *CommandText*のパラメーター、**接続**オブジェクトの[Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)メソッド、および、 *ソース*のパラメーター、 **Recordset**オブジェクトの[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドです。  
  
 相対 URL で指定できる、 *CommandText*または*ソース*パラメーター。 相対 URL が、SQL コマンド; などのコマンドを実際に表していませんパラメーターだけを指定します。 アクティブな接続のコンテキストは、絶対 URL である必要があります、*オプション*にパラメーターを設定する必要があります**adCmdTableDirect**です。  
  
 たとえば、次のコード サンプルを開く方法を示しています。、 **Recordset** Winnt/system32 ディレクトリの Readme25.txt ファイル。  
  
```  
recordset.Open "system32/Readme25.txt", "URL=http://YourServer/Winnt/",,,adCmdTableDirect  
```  
  
 接続文字列の絶対 URL が、サーバーを指定します (`YourServer`) およびパス (`Winnt`)。 この URL は、コンテキストにも定義します。  
  
 コマンド テキスト内の相対 URL が開始点として絶対 URL を使用し、パスの残りの部分を指定します (`system32`) と、ファイルを開く (`Readme25.txt`)。  
  
 [オプション] フィールド (`adCmdTableDirect`) コマンドの種類が相対 URL であることを示します。  
  
 次のコードを開く別の例として、 **Recordset**の内容に、`Winnt`ディレクトリ。  
  
```  
recordset.Open "", "URL=http://YourServer/Winnt/",,,adCmdTableDirect  
```  
  
## <a name="ole-db-provider-supplied-url-schemes"></a>OLE DB プロバイダーが指定した URL パターン  
 完全修飾 URL の先頭部分は、*スキーム*URL の残りの部分で識別されるリソースへのアクセスに使用されます。 例については、HTTP (ハイパー テキスト転送プロトコル) と FTP (ファイル転送プロトコル) です。  
  
 ADO では、独自の URL スキームを認識する OLE DB プロバイダーをサポートします。 たとえば、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)*、* 「公開済み」の Windows 2000 のファイルにアクセスする既存の HTTP スキームを認識します。  
  
## <a name="see-also"></a>参照  
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)

