---
title: "SQL Server 識別子のエンコードとデコード | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# SQL Server 識別子のエンコードとデコード
  SQL Server の区切られた識別子には、Windows PowerShell パスでサポートされない文字が含まれる場合があります。 これらの文字は、16 進数値にエンコードすることによって指定できます。  
  
1.  **作業を開始する準備:**  [制限事項と制約事項](#LimitationsRestrictions)  
  
2.  **特殊文字を処理する方法:**  [識別子のエンコード](#EncodeIdent)、 [識別子のデコード](#DecodeIdent)  
  
## はじめに  
 Windows PowerShell パス名でサポートされない文字は、"**%**xx" のように、"%" 文字の後に文字を表すビット パターンの 16 進値を付加して表す、つまりエンコードすることができます。 エンコードは、Windows PowerShell パスでサポートされない文字を処理する場合にいつでも使用できます。  
  
 **Encode-SqlName** コマンドレットは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 識別子を入力として受け取ります。 また、Windows PowerShell 言語ではサポートされないすべての文字が "%xx" でエンコードされた文字列を出力します。 **Decode-SqlName** コマンドレットは、エンコードされた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 識別子を入力として受け取り、元の識別子を返します。  
  
###  <a name="LimitationsRestrictions"></a> 制限事項と制約事項  
 **Encode-Sqlname** コマンドレットと **Decode-Sqlname** コマンドレットでエンコードまたはデコードできるのは、SQL Server の区切られた識別子ではサポートされるものの PowerShell パスではサポートされない文字のみです。 **Encode-SqlName** によってエンコードされ、**Decode-sqlname** によってデコードされる文字を次に示します。  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|**文字**|\|/|[ ] :|%|\<|>|*|?|[|]|&#124;|  
|**16 進エンコード**|%5C|%2F|%3A|%25|%3C|%3E|%2A|%3F|%5B|%5D|%7C|  
  
##  <a name="EncodeIdent"></a> 識別子のエンコード  
 **PowerShell パス内で SQL Server 識別子をエンコードするには**  
  
-   SQL Server 識別子をエンコードするには、次の 2 つの方法のいずれかを使用します。  
  
    -   サポートされていない文字の 16 進数コードを、%XX という構文 (XX は 16 進数コード) を使用して指定します。  
  
    -   識別子を引用符で囲まれた文字列として **Encode-Sqlname** コマンドレットに渡します。  
  
### 例 (エンコード)  
 この例では、":" 文字のエンコードされたバージョン (%3A) を指定します。  
  
```  
Set-Location Table%3ATest  
```  
  
 あるいは、**Encode-SqlName** を使用して Windows PowerShell でサポートされる名前を作成できます。  
  
```  
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="DecodeIdent"></a> 識別子のデコード  
 **PowerShell パスの SQL Server 識別子をデコードするには**  
  
 16 進数エンコードを、そのエンコードが表す文字に置換するには、**Decode-Sqlname** コマンドレットを使用します。  
  
### 例 (デコード)  
 次の例は、"Table:Test" を返します。  
  
```  
Decode-SqlName "Table%3ATest"  
```  
  
## 参照  
 [PowerShell での SQL Server 識別子](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell プロバイダー](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  