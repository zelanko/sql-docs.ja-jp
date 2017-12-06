---
title: "SSMA MySQL コンソール (MySQLToSQL) 用の操作 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 240aaad1-d65d-4dea-b60b-315cb1ac733d
caps.latest.revision: "19"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1722db6c7325c10099cd293e6b8c102c38874692
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="working-with-ssma-for-mysql-console-mysqltosql"></a>SSMA MySQL コンソール (MySQLToSQL) 用の操作
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) for MySQL では、コマンドラインで、コンソール アプリケーションからアクセスできるようになりました。 スクリプト ファイルは、コマンドを実行するためのアプリケーションへの入力を形成します。 コンソール アプリケーションとして SSMA スクリプト レベルのやり取りを有効に、移行サイクルが減少し、移行作業のスケールを設定します。  
  
このセクションでは、SSMA コンソール アプリケーションを使用して、MySQL データベースを移行する手順について説明します。  
  
このセクションで説明されているトピックは次のとおりです。  
  
|||  
|-|-|  
|**トピック**|**Description**|  
|[MySQL コンソール &#40; for SSMA の概要MySQLToSQL &#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-console-mysqltosql.md)|コンソール アプリケーションを実行する手順について説明します。|  
|[SSMA コンソール &#40; コマンド ライン オプションMySQLToSQL &#41;](../../ssma/mysql/command-line-options-in-ssma-console-mysqltosql.md)|SSMA コンソール アプリケーションを操作するには、コマンド ライン オプションとパラメーターについて説明します。|  
|[スクリプト ファイル &#40; を作成します。MySQLToSQL &#41;](../../ssma/mysql/creating-script-files-mysqltosql.md)|スクリプト ファイルを作成する方法について説明します。|  
|[変数値ファイル &#40; を作成します。MySQLToSQL &#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)|変数値ファイルを作成する方法について説明します。|  
|[サーバーの接続ファイル &#40; を作成します。MySQLToSQL &#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)|サーバー接続ファイルを作成する方法について説明します。|  
|[SSMA コンソール &#40; を実行します。MySQLToSQL &#41;](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md)|SSMA コンソール アプリケーションを操作するコマンドをスクリプト ファイルについて説明します。|  
|[サンプルのコンソールのスクリプト ファイル &#40; の操作MySQLToSQL &#41;](../../ssma/mysql/working-with-the-sample-console-script-files-mysqltosql.md)|製品と共にファイルのサンプルで提供されているスクリプトを簡単にカスタマイズする方法について説明します|  
|[パスワード &#40; を管理します。MySQLToSQL &#41;](../../ssma/mysql/managing-passwords-mysqltosql.md)|パスワードの暗号化と復号化、およびインポート/エクスポートのパスワードの情報について説明します。|  
|[生成するレポートと #40 です。MySQLToSQL &#41;](../../ssma/mysql/generating-reports-mysqltosql.md)|レポートを生成するコマンドを一覧表示します。|  
|[トラブルシューティング (&) #40 です。MySQLToSQL &#41;](../../ssma/mysql/troubleshooting-mysqltosql.md)|移行に関する問題の解決方法に関する簡単な情報を提供します。|  
  
## <a name="see-also"></a>参照  
[MySQL コンソール for SSMA の概要](http://msdn.microsoft.com/en-us/218d502c-059f-4d48-9aea-61e553d74303)  
  
