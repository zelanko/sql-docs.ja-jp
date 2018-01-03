---
title: "変数値ファイル (SybaseToSQL) を作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Creating Variable Value Files
- Sybase Console,Variable Value File Validation
ms.assetid: 395be464-4b19-44f7-91e5-b8876d6743dc
caps.latest.revision: "15"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 28fadfc4f54f68a6459cc3f3cef4df91967e5e52
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="creating-variable-value-files-sybasetosql"></a>変数値ファイル (SybaseToSQL) を作成します。
変数の値ファイルと同様に、送信元または送信先のサーバー名に 1 つのサーバーの移行を頻繁に変更するコマンドのパラメーター値で構成される XML ファイルです。 多数のデータベースの移行が発生すると、各送信元サーバーの値を格納するための複数の変数ファイルが作成されでマスター スクリプト ファイルで参照されている、 **– v**コマンド ライン スイッチです。 これは、複数の変数ファイルで変数の値を持ついくつかのスクリプト ファイルの静的な値を維持するために役立ちます。  
  
> [!NOTE]  
> 1.  変数の名前が始まるし、$ (ドル) 記号が付加されたものです。 変数が変数の値のファイルの値を割り当てられていない場合は、コンソールの実行プロセスの停止の結果として得られるスクリプト ファイルの解析中にエラーが発生します。  
> 2.  The escape character for **$** is **$$**. パラメーターの変数または静的な値の値を含むかどうか **$** し (ドル) シンボル **$$** 変数の代わりに文字として扱うことを示す指定する必要があります。  
> 3.  保守容易性のために、変数内で宣言できます`‘variable-group’`ユーザーの論理的な分離の要素は、変数を定義します。  この要素の使用は必須ではありません。  
  
**使用例:**  
  
**例 1:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<project-folder>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**例 2:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="variable-value-file-validation"></a>変数の値のファイルの検証  
ユーザーがスキーマ定義ファイルに対して自分の変数値ファイルを簡単に検証**ConsoleScriptVariablesSchema.xsd** 'スキーマ' フォルダー内にあります。  
  
## <a name="next-step"></a>次の手順  
コンソールの運用には、次の手順は[サーバー接続ファイル &#40; を作成します。SybaseToSQL &#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
## <a name="see-also"></a>参照  
[サーバー ファイル (Sybase) を作成します。](http://msdn.microsoft.com/en-us/35ef396f-9f98-429d-9fc5-4f413d08fb37)  
  
