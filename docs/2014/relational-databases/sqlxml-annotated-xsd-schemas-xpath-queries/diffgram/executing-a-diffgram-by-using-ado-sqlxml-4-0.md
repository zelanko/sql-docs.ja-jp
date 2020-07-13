---
title: ADO を使用した DiffGram の実行 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], SQLOLEDB Provider
- ADO [SQLXML]
- SQLXMLOLEDB Provider, DiffGrams
- data providers [SQLXML], SQLOLEDB Provider
- DiffGrams [SQLXML], ADO
ms.assetid: 741fce82-de83-4923-86eb-30acb5b9a5e6
author: rothja
ms.author: jroth
ms.openlocfilehash: 304cba3b913e9eb16d25af58f303945ec882266c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062976"
---
# <a name="executing-a-diffgram-by-using-ado-sqlxml-40"></a>ADO を使用した、DiffGram の実行 (SQLXML 4.0)
  この [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic アプリケーションでは、ADO を使用して Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を確立した後、DiffGram を実行します。 このアプリケーションでは、DiffGram と XSD スキーマは 1 つのファイルに格納されており、 ファイルを指定して DiffGram を読み込みます。 [Diffgram の例](diffgram-examples-sqlxml-4-0.md)に記載されている、すべての diffgram (および関連する XSD スキーマ) を使用できます。  
  
 サンプルアプリケーションのプロセスは次のとおりです。  
  
-   **Conn**オブジェクト (**ADODB接続**) 特定のサーバー上の SQL Server の実行中のインスタンスへの接続を確立します。  
  
-   **Cmd**オブジェクト (**ADODB**) は、確立された接続で実行されます。  
  
-   コマンド言語が DBGUID_MSSQLXML に設定されます。  
  
-   DiffGram は、ファイルからコマンドストリーム (**Strmin**) にコピーされます。  
  
-   コマンドの出力ストリームは、 **Strmout**オブジェクト (ADODB) に設定され**ます。ストリーム**) が返されます。  
  
-   SQLOLEDB プロバイダーを使用する場合、既定では Sqlxmlx.dll により Microsoft SQLXML の機能が提供されます。 SQLOLEDB プロバイダーで Sqlxml4.dll を使用するには、SQLOLEDB プロバイダー**接続**オブジェクトで**sqlxml Version**プロパティを**sqlxml. 4.0**に設定する必要があります。  
  
-   コマンド (DiffGram) が実行されます。  
  
 サンプル アプリケーションのコードを次に示します。  
  
> [!NOTE]  
>  コードでは、接続文字列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。  
  
```  
Private Sub Command1_Click()  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmOut As New ADODB.Stream  
  Dim strmIn As New ADODB.Stream  
  
  'Open a connection to SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=SqlServerName; database=tempdb; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  strmIn.Open  
  strmIn.Charset = "UTF-8"  
  strmIn.LoadFromFile "C:\SomeFilePath\SampleDiffGram.xml"  
  strmIn.Position = 0  
  Set cmd.CommandStream = strmIn  
  
  strmOut.Open  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  cmd.Properties("Mapping Schema") = "C:\SomeFilePath\SampleDiffGram.xml"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Set cmd = Nothing  
  strmOut.Charset = "UTF-8"  
  strmOut.SaveToFile "C:\DropIt.txt", adSaveCreateOverWrite  
  strmOut.Close  
  Set strmOut = Nothing  
  
End Sub  
```  
  
### <a name="to-test-the-diffgram"></a>DiffGram をテストするには  
  
1.  コンピューター上のフォルダーには、 [diffgram の例](diffgram-examples-sqlxml-4-0.md)のいずれかの例から、いずれかの diffgram と対応する XSD スキーマをコピーします。  
  
2.  Visual Basic を開き、標準 EXE プロジェクトを作成します。  
  
3.  プロジェクトに次の参照を追加します。  
  
    ```  
    Microsoft ActiveX Data Objects 2.8 Library  
    ```  
  
4.  ツールボックスで、[**コマンド**ボタン] をクリックし、フォームにボタンを描画します。  
  
5.  ボタンをダブルクリックしてコードを編集し、トピックで提供されるアプリケーション コードを追加します。  
  
6.  コードに DiffGram と XSD ファイルの名前を指定し、 接続文字列も適宜変更します。  
  
7.  アプリケーションを実行します。 実行結果は、実行する DiffGram によって変わります。  
  
  
