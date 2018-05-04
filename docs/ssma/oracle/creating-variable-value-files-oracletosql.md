---
title: 変数値ファイル (OracleToSQL) を作成する |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Variable Value File Creation
- Variable Value File, Variable Value File Validation
ms.assetid: f583d81a-8e34-41b1-8100-ee3a6a82213b
caps.latest.revision: 26
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: badf497279446ec24aada8f27e5f999c87d4f7a0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="creating-variable-value-files-oracletosql"></a>変数値ファイル (OracleToSQL) を作成します。
変数の値ファイルと同様に、送信元または送信先のサーバー名に 1 つのサーバーの移行を頻繁に変更するコマンドのパラメーター値で構成される XML ファイルです。 多数のデータベースの移行が発生すると、各送信元サーバーの値を格納するための複数の変数ファイルが作成されでマスター スクリプト ファイルで参照されている、 **– v**コマンド ライン スイッチです。 これは、複数の変数ファイルで変数の値を持ついくつかのスクリプト ファイルの静的な値を維持するために役立ちます。  
  
> [!NOTE]  
> 1.  変数の名前が始まるし、$ (ドル) 記号が付加されたものです。 変数が変数の値のファイルの値を割り当てられていない場合は、コンソールの実行プロセスの停止の結果として得られるスクリプト ファイルの解析中にエラーが発生します。  
> 2.  The escape character for **$** is **$$**. パラメーターの変数または静的な値の値を含むかどうか**$** し (ドル) シンボル**$$** 変数の代わりに文字として扱うことを示す指定する必要があります。  
> 3.  保守容易性のために、変数内で宣言できます`‘variable-group’`ユーザーの論理的な分離の要素は、変数を定義します。  この要素の使用は必須ではありません。  
  
**例 :**  
  
**例 1:**  
  
```  
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
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
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
  
## <a name="next-step"></a>次の手順  
コンソールの運用には、次の手順は[サーバー接続ファイルを作成する&#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
## <a name="see-also"></a>参照  
[サーバー ファイル (Oracle) を作成します。](http://msdn.microsoft.com/en-us/002f129e-0868-48ad-a4b4-c68b5007e12e)  
  
