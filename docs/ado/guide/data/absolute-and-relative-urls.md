---
title: 絶対 Url と相対 Url |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- relative URLs [ADO]
- absolute URLs [ADO]
- URLs [ADO]
ms.assetid: 6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f15c5890300687a2d587a58a586d00bf2c8d0fd8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926360"
---
# <a name="absolute-and-relative-urls"></a>絶対 URL と相対 URL
URL は、ローカルまたはネットワーク上のコンピューターに格納されているターゲットの場所を指定します。 ターゲットには、ファイル、ディレクトリ、HTML ページ、イメージ、プログラムなどがあります。  
  
 *絶対 URL*には、リソースを検索するために必要なすべての情報が含まれています。  
  
 *相対 url*は、開始点として絶対 url を使用してリソースを検索します。 実際には、ターゲットの "完全な URL" は、絶対 Url と相対 Url を連結することによって指定されます。  
  
 *絶対 URL*は、次の形式を使用します: *scheme://server/path/resource*  
  
 相対 URL は、通常、*パス*と、必要に応じて*リソース*だけで構成されますが、*スキーム*や*サーバー*は含まれません。 次の表は、完全な URL 形式の個々の部分を定義しています。  
  
 *体系*  
 *リソース*へのアクセス方法を指定します。  
  
 *server*  
 *リソース*が配置されているコンピューターの名前を指定します。  
  
 *path*  
 ターゲットにつながる一連のディレクトリを指定します。 *リソース*を省略した場合、ターゲットは*path*の最後のディレクトリになります。  
  
 *resource*  
 含まれている場合、*リソース*はターゲットであり、通常はファイルの名前です。 これは、1つのバイナリストリーム (バイト) を含む*単純なファイル*であるか、または1つ以上のストレージとバイトのバイナリストリームを含む*構造化ドキュメント*である可能性があります。  
  
## <a name="url-scheme-registration"></a>URL スキームの登録  
 プロバイダーが Url をサポートしている場合は、プロバイダーによって1つ以上の URL スキームが登録されます。 登録とは、スキームを使用するすべての Url が、登録されているプロバイダーを自動的に呼び出すことを意味します。 たとえば、 *http*スキームは、[インターネット発行用に Microsoft OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)に登録されています。 ADO では、"http" で始まるすべての Url が、インターネット発行プロバイダーで使用される Web フォルダーまたはファイルを表していると想定しています。 プロバイダーによって登録されたスキームの詳細については、プロバイダーのドキュメントを参照してください。  
  
## <a name="defining-context-with-a-url"></a>URL を使用してコンテキストを定義する  
 [接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトによって表される開いている接続の機能の1つは、その接続で表されるデータソースに対する後続の操作を制限することです。 つまり、接続は後続の操作のコンテキストを定義します。  
  
 ADO 2.7 以降では、絶対 URL でコンテキストを定義することもできます。 たとえば、絶対 URL で[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトを開くと、url で指定されたリソースを表す**接続**オブジェクトが暗黙的に作成されます。  
  
 コンテキストを定義する絶対 URL は、 **Record**オブジェクト[Open](../../../ado/reference/ado-api/open-method-ado-record.md)メソッドの*ActiveConnection*パラメーターで指定できます。 絶対 URL は、 **Connection**オブジェクト[open](../../../ado/reference/ado-api/open-method-ado-connection.md) method *ConnectionString*パラメーターの "URL =" キーワードの値として指定することもできます。また、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト[open](../../../ado/reference/ado-api/open-method-ado-recordset.md) method *ActiveConnection* parameter を指定することもできます。  
  
 また、ディレクトリを表す**レコード**または**レコードセット**オブジェクトを開くことによってコンテキストを定義することもできます。これらのオブジェクトには、コンテキストを指定する暗黙的または明示的に宣言された**接続**オブジェクトが既に存在しているためです。  
  
## <a name="scoped-operations"></a>スコープ指定操作  
 コンテキストでは、スコープ (つまり、後続の操作に参加できるディレクトリとそのサブディレクトリ) も定義されています。 **レコード**オブジェクトには、ディレクトリとそのすべてのサブディレクトリに対して操作を実行するスコープ付きメソッドがいくつかあります。 これらのメソッドには、 [Copyrecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)、 [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)、および[DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)が含まれます。  
  
## <a name="relative-urls-as-command-text"></a>コマンドテキストとしての相対 Url  
 **接続**オブジェクトの[Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)メソッドの*CommandText*パラメーターに文字列を入力し、**レコードセット**オブジェクトの[Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドの*source*パラメーターに文字列を入力することにより、データソースに対して実行するコマンドを指定できます。  
  
 相対 URL は、 *CommandText*または*Source*パラメーターで指定できます。 相対 URL は、実際には SQL コマンドなどのコマンドを表していません。パラメーターを指定するだけです。 アクティブな接続のコンテキストは絶対 URL である必要があり、*オプション*パラメーターは**Adcmdtabledirect**に設定する必要があります。  
  
 たとえば、次のコードサンプルは、Winnt/system32 ディレクトリの Readme25 ファイルで**レコードセット**を開く方法を示しています。  
  
```  
recordset.Open "system32/Readme25.txt", "URL=https://YourServer/Winnt/",,,adCmdTableDirect  
```  
  
 接続文字列の絶対 URL は、サーバー (`YourServer`) とパス (`Winnt`) を指定します。 この URL は、コンテキストも定義します。  
  
 コマンドテキストの相対 URL は、絶対 URL を開始点として使用し、パスの残りの部分`system32`() と開くファイル (`Readme25.txt`) を指定します。  
  
 Options フィールド (`adCmdTableDirect`) は、コマンドの種類が相対 URL であることを示します。  
  
 もう1つの例として、次のコードでは、 `Winnt`ディレクトリの内容に対して**レコードセット**を開きます。  
  
```  
recordset.Open "", "URL=https://YourServer/Winnt/",,,adCmdTableDirect  
```  
  
## <a name="ole-db-provider-supplied-url-schemes"></a>プロバイダーが指定した URL スキームの OLE DB  
 完全修飾 URL の先頭部分は、URL の残りの部分で識別されるリソースにアクセスするために使用される*スキーム*です。 例として、HTTP (ハイパーテキスト転送プロトコル) および FTP (ファイル転送プロトコル) があります。  
  
 ADO では、独自の URL スキームを認識する OLE DB プロバイダーがサポートされています。 たとえば、"公開済み" の Windows 2000*ファイルにアクセスする、* [インターネット公開用の Microsoft OLE DB Provider](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)は、既存の HTTP スキームを認識します。  
  
## <a name="see-also"></a>参照  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
