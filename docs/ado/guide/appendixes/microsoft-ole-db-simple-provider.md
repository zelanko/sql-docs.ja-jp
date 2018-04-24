---
title: Microsoft OLE DB の単純なプロバイダー |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- simple provider [ADO]
- providers [ADO], OLE DB simple provider
- OLE DB simple provider [ADO]
ms.assetid: 1e7dc6f0-482c-4103-8187-f890865e40fc
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b7e4a5742b9d5b084d10540737ac87c55d441d0a
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-ole-db-simple-provider-overview"></a>Microsoft OLE DB プロバイダーの簡単な概要
Microsoft OLE DB 単純なプロバイダー (OSP) により、対象のプロバイダーが書き込まれたを使用して任意のデータにアクセスする ADO、 [OLE DB 単純なプロバイダー (OSP) Toolkit](http://msdn.microsoft.com/en-us/6e7b7931-9e4a-4151-ae51-672abd3f84a6)です。 単純なプロバイダーは、インメモリ配列、または XML ドキュメントなどの基本的な OLE DB のサポートを必要とするデータ ソースにアクセスするものです。

## <a name="connection-string-parameters"></a>接続文字列パラメーター
 OLE DB 単純なプロバイダーの DLL に接続するには、設定、*プロバイダー*への引数、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)プロパティ。

```
MSDAOSP
```

 この値も設定またはを使用して読み取る、[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティです。

 プロバイダーの作成者によって決定されます、登録済みのプロバイダー名を使用してすべての OLE DB プロバイダーとして登録されている単純なプロバイダーに接続することができます。

## <a name="typical-connection-string"></a>一般的な接続文字列
 このプロバイダーの一般的な接続文字列とは。

```
"Provider=MSDAOSP;Data Source=serverName"
```

 文字列は、これらのキーワードで構成されます。

|Keyword|Description|
|-------------|-----------------|
|**プロバイダー**|SQL Server の OLE DB プロバイダーを指定します。|
|**[データ ソース]**|サーバーの名前を指定します。|

## <a name="xml-document-example"></a>XML ドキュメントの例
 OLE DB 単純なプロバイダー (OSP) MDAC 2.7 以降および Windows Data Access Components (Windows DAC) が階層的な ADO を開くことがサポートする強化されました**レコード セット**を任意の XML ファイルです。 これらの XML ファイルは、ADO の XML 永続性スキーマを含めることがありますが、必須ではありません。 OSP に接続することによってこれが実装されて、 **MSXML2.DLL**。 したがって**MSXML2.DLL**以降が必要です。

 **Portfolio.xml**次の例で使用されるファイルには、次のようなツリーが含まれています。

```
Portfolio
   Stock
      Shares
      Symbol
      Price
      Info
         Company Name
         WebSite
```

 XML DSO では、組み込みのヒューリスティックを使用して、XML ツリー内のノードを階層構造のチャプターに変換**Recordset**です。

 これらの組み込みのヒューリスティックを使用して、XML ツリーは、2 レベルの階層に変換される**Recordset**次の形式。

```
Parent Recordset
Shares, Symbol, Price, $Text
   Child Recordset
      Company Name, WebSite, $Text
```

 ポートフォリオ、および情報のタグは、階層で表されないことに注意してください**Recordset**です。 XML DSO に階層を XML ツリーを変換する方法の詳細について**レコード セット**、次の規則を参照してください。 $Text 列は、次のセクションで説明しています。

## <a name="rules-for-assigning-xml-elements-and-attributes-to-columns-and-rows"></a>XML 要素の割り当てと属性を行と列のルール
 XML DSO では、要素を割り当てるための手順に依存して、属性列とデータにバインドされたアプリケーション内の行。 XML は、階層全体を含んでいる 1 つのタグを含むツリーとしてモデル化されます。 たとえば、書籍の XML 表記の説明には、章タグ、図のタグ、およびセクション タグが含まれます。 最高レベルのタグになります、書籍、サブ要素章、図、およびセクションを含むです。 XML DSO では、行と列に XML 要素をマップ、トップ レベル要素ではなく、サブ要素が変換されます。

 XML DSO は、サブ要素を変換するため、この手順を使用します。

-   各サブ要素と属性がいくつかの列に対応する**レコード セット**階層にします。

-   列の名前がサブ要素または属性の名前と同じ親要素には、後者して、同じ名前のサブ要素の属性があるない限り、"!"サブ要素の列名に付加します。

-   各列は、いずれか、*単純*スカラー値 (通常の文字列) を含む列または**レコード セット**子が含まれる列**レコード セット**です。

-   属性に対応する列は常に単純です。

-   サブ要素に対応する列は**Recordset**列の場合は、サブ要素に独自のサブ要素または属性 (または両方)、またはサブ要素の親は子としてサブ要素の 1 つ以上のインスタンスのいずれか。 それ以外の場合、列は簡単です。

-   (別の親) の下のサブ要素の複数のインスタンスが存在する場合、その列は、 **Recordset**列場合*任意*インスタンスの意味、**レコード セット**列です。列が単純な場合にのみ、*すべて*インスタンスが単純な列を意味します。

-   すべて**レコード セット**ある $Text という列を追加します。

 構築するために必要なコード、 **Recordset**のとおりです。

```
Dim adoConn as ADODB.Connection
Dim adoRS as ADODB.Recordset

Set adoRS = New ADODB.Connection
Set adoRS = New ADODB.Recordset

adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
adoRS.Open "http://WebServer/VRoot/portfolio.xml, adoConn
```

> [!NOTE]
>  4 つの異なる名前付け規則を使用してデータ ファイルのパスを指定することができます。

```
'HTTP://
adoRS.Open "http://WebServer/VRoot/portfolio.xml", adoConn
'FILE://
adoRS.Open "file:/// C:\\Directory\\portfolio.xml", adoConn
'UNC Path
adoRS.Open "\\ComputerName\ShareName\portfolio.xml", adoConn
'Full DOS Path
adoRS.Open "C:\Directory\portfolio.xml", adoConn
```

 すぐに、 **Recordset**が開かれて、通常、ADO **Recordset**ナビゲーション コマンドを使用できます。

 **レコード セット**OSP によって生成されたいくつかの制限があります。

-   クライアント カーソル (**adUseClient**) はサポートされていません。

-   階層**レコード セット**任意で作成された XML を保存できませんを使用して**Recordset.Save**です。

-   **レコード セット**OSP で作成された読み取り専用です。

-   XMLDSO 列が追加されてデータ $Text のそれぞれに**Recordset**階層にします。

 OLE DB 単純なプロバイダーの詳細については、次を参照してください。[単純なプロバイダーを構築](http://msdn.microsoft.com/en-us/b31a6cba-58ae-4ee8-9039-700973d354d6)です。

## <a name="code-example"></a>コード例
 Visual Basic コードを次に示します、階層構造を構築する、任意の XML ファイルを開く**レコード セット**、およびそれぞれの各レコードの書き込みを再帰的に**レコード セット**デバッグ ウィンドウにします。

 ここでは、株価情報を含む単純な XML ファイルです。 次のコードでは、このファイルを使用して、2 つのレベル階層を構築**Recordset**です。

```
<portfolio>
   <stock>
      <shares>100</shares>
      <symbol>MSFT</symbol>
      <price>$70.00</price>
      <info>
         <companyname>Microsoft Corporation</companyname>
         <website>http://www.microsoft.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>AAPL</symbol>
      <price>$107.00</price>
      <info>
         <companyname>Apple Computer, Inc.</companyname>
         <website>http://www.apple.com</website>
      </info>
   </stock>
   <stock>
      <shares>100</shares>
      <symbol>DELL</symbol>
      <price>$50.00</price>
      <info>
         <companyname>Dell Corporation</companyname>
         <website>http://www.dell.com</website>
      </info>
    </stock>
    <stock>
       <shares>100</shares>
       <symbol>INTC</symbol>
       <price>$115.00</price>
       <info>
          <companyname>Intel Corporation</companyname>
          <website>http://www.intel.com</website>
       </info>
   </stock>
</portfolio>
```

 2 つの Visual Basic sub プロシージャを次に示します。 最初の作成、 **Recordset**に渡します、 *WalkHier* sub プロシージャ、再帰的には、下の階層は、それぞれの書き込みでは説明**フィールド**各内の各レコードで**Recordset**デバッグ ウィンドウにします。

```
Private Sub BrowseHierRecordset()
' Add ADO 2.7 or later to Project/References
' No need to add MSXML2, ADO just passes the ProgID through to the OSP.

    Dim adoConn As ADODB.Connection
    Dim adoRS As ADODB.Recordset
    Dim adoChildRS As ADODB.Recordset

    Set adoConn = New ADODB.Connection
    Set adoRS = New ADODB.Recordset
    Set adoChildRS = ADODB.Recordset

    adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
    adoRS.Open "http://bwillett3/Kowalski/portfolio.xml", adoConn

    Dim iLevel As Integer
    iLevel = 0
    WalkHier iLevel, adoRS

End Sub

Sub WalkHier(ByVal iLevel As Integer, ByVal adoRS As ADODB.Recordset)
    iLevel = iLevel + 1
    PriorLevel = iLevel
    While Not adoRS.EOF
        For ndx = 0 To adoRS.Fields.Count - 1
            If adoRS.Fields(ndx).Name <> "$Text" Then
                If adoRS.Fields(ndx).Type = adChapter Then
                    Set adoChildRS = adoRS.Fields(ndx).Value
                    WalkHier iLevel, adoChildRS
                Else
                    Debug.Print iLevel & ": adoRS.Fields(" & ndx & _
                       ") = " & adoRS.Fields(ndx).Name & " = " & _
                       adoRS.Fields(ndx).Value
                End If
            End If
        Next ndx
        adoRS.MoveNext
    Wend
    iLevel = PriorLevel
End Sub
```
