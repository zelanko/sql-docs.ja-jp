---
title: SSMA Sybase コンソール (SybaseToSQL) 用の操作 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: c465e477-c479-4aa8-918d-58bf30884789
caps.latest.revision: 19
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5eaf03b7dc78b90f836ded87d69c1a6a7350453c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-ssma-for-sybase-console-sybasetosql"></a>SSMA Sybase コンソール (SybaseToSQL) 用の操作
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA)、リリースの Sybase Adaptive Server Enterprise (ASE) は、コマンドラインで、コンソール アプリケーションからアクセスできるようになりました。 スクリプト ファイルは、コマンドを実行するためのアプリケーションへの入力を形成します。 コンソール アプリケーションとして SSMA スクリプト レベルのやり取りを有効に、移行サイクルが減少し、移行作業のスケールを設定します。  
  
このセクションでは、SSMA コンソール アプリケーションを使用して、ASE データベースを移行する手順について説明します。  
  
このセクションで説明されているトピックは次のとおりです。  
  
|||  
|-|-|  
|**トピック**|**Description**|  
|[Sybase コンソール for SSMA の概要&#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-console-sybasetosql.md)|コンソール アプリケーションを実行する手順について説明します。|  
|[SSMA コンソールでのコマンド ライン オプション&#40;SybaseToSQL&#41;](../../ssma/sybase/command-line-options-in-ssma-console-sybasetosql.md)|SSMA コンソール アプリケーションを操作するには、コマンド ライン オプションとパラメーターについて説明します。|  
|[スクリプト ファイルを作成する&#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md)|スクリプト ファイルを作成する方法について説明します。|  
|[変数の値のファイルを作成する&#40;SybaseToSQL&#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)|変数値ファイルを作成する方法について説明します。|  
|[サーバー接続ファイルを作成する&#40;SybaseToSQL&#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)|サーバー接続ファイルを作成する方法について説明します。|  
|[SSMA コンソールを実行する&#40;SybaseToSQL&#41;](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md)|SSMA コンソール アプリケーションを操作するコマンドをスクリプト ファイルについて説明します。|  
|[サンプルのコンソールのスクリプト ファイルで作業&#40;SybaseToSQL&#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)|製品と共にファイルのサンプルで提供されているスクリプトを簡単にカスタマイズする方法について説明します|  
|[パスワードを管理する&#40;SybaseToSQL&#41;](../../ssma/sybase/managing-passwords-sybasetosql.md)|パスワードの暗号化と復号化、およびインポート/エクスポートのパスワードの情報について説明します。|  
|[レポートの生成&#40;SybaseToSQL&#41;](../../ssma/sybase/generating-reports-sybasetosql.md)|レポートを生成するコマンドを一覧表示します。|  
|[トラブルシューティング&#40;SybaseToSQL&#41;](../../ssma/sybase/troubleshooting-sybasetosql.md)|移行に関する問題の解決方法に関する簡単な情報を提供します。|  
  
## <a name="see-also"></a>参照  
[Sybase Console(SybaseToSQL) for SSMA の概要](http://msdn.microsoft.com/en-us/43219dbe-bcfa-427d-9242-f07b1455f15f)  
  
