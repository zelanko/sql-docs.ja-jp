---
title: "変数値ファイル (AccessToSQL) を作成する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 808595c3-8ef1-40bd-a93e-5cf237950e08
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: b7ccb1d92b39d41ec3fa961b03b33c229a274af0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/17/2017

---
# <a name="creating-variable-value-files-accesstosql"></a>変数値ファイル (AccessToSQL) を作成します。
変数値ファイルは、サーバーの移行の間で頻繁に変更 (送信元または送信先のサーバー名) などのコマンドのパラメーター値で構成される XML ファイルです。 多数のデータベースの移行が発生すると、各送信元サーバーの値を格納するための複数の変数ファイルが作成されでマスター スクリプト ファイルで参照されている、 **– v**コマンド ライン スイッチです。 この動作は、複数の変数ファイルで変数の値を持ついくつかのスクリプト ファイルの静的な値を維持する上で役立ちます。  
  
> [!NOTE]  
> -  変数の名前が始まるし、$ (ドル) 記号が付加されたものです。 変数に変数の値のファイルの値が割り当てられていない場合、スクリプト ファイルの解析中にエラーが発生、その結果、コンソールの実行プロセスの停止にします。  
> -  The escape character for **$** is **$$**. パラメーターの変数または静的な値の値が含まれている場合、  **$** し (ドル) シンボル **$$** 変数の代わりに文字として扱うことを示す指定する必要があります。  
> -  保守容易性のために、変数内で宣言できます`‘variable-group’`ユーザー定義変数の論理的な分離の要素。  この要素の使用は必須ではありません。  
  
**例 :**  
  
**例 1:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$type$" value="MyProject"/>  
  
    <variable name="$project_folder$" value=".\$project_name$"/>  
  
    <variable name="$project_name$" value="$type$ConsoleProject"/>  
  
    <variable name="$project_overwrite$" value="true"/>  
  
    <variable name="$project_type$" value="sql-server-2008"/>  
  
  </variable-group>  
  
</variables>  
```  
**例 2:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="xxx"/>  
  
      <variable name="$TargetDB$" value="xxx"/>  
  
      <variable name="$TargetUserName$" value="xxx"/>  
  
      <variable name="$TargetPassword$" value="xxx"/>  
  
      <variable name="$TargetIsTrusted$" value="xxx"/>  
  
      <variable name="$TrustedConnection$" value="xxx"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="TestTable1"/>  
  
      <variable name="$ObjectName2$" value="TestProc1"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="variable-value-file-validation"></a>変数の値のファイルの検証  
ユーザーがスキーマ定義ファイルに対して自分の変数値ファイルを簡単に検証**ConsoleScriptVariablesSchema.xsd** 'スキーマ' フォルダー内にあります。  
  
## <a name="next-step"></a>次の手順  
コンソールの運用には、次の手順は[サーバー接続ファイル &#40; を作成します。AccessToSQL &#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
## <a name="see-also"></a>参照  
[サーバー接続ファイル (アクセス) を作成します。](http://msdn.microsoft.com/829153be-aa8e-4162-87e8-69882feecf19)  
  

