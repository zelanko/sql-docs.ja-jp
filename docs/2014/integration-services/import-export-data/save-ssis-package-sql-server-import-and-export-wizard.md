---
title: '[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8b8ef62839d7379c35b55af7bcb65ab46e4b455d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048233"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>[SSIS パッケージの保存]\(SQL Server インポートおよびエクスポート ウィザード)
  使用して、 **SSIS パッケージの保存**名前、説明、および保存するページ、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration Services ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) にパッケージ化、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb`データベースまたはファイルを持つ、.dtsx拡張機能。  
  
> [!NOTE]  
>  [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]、ウィザードによって作成されたパッケージを保存するオプションは使用できません。  
  
 このウィザードの詳細については、次を参照してください。 [SQL Server インポートおよびエクスポート ウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)します。 ウィザードを正常に実行するために必要なアクセス許可と、ウィザードを起動するオプションについて説明しますを参照してください。 [、SQL Server インポートおよびエクスポート ウィザードを実行](start-the-sql-server-import-and-export-wizard.md)します。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **名前**  
 パッケージの一意な名前を指定します。  
  
 **[説明]**  
 パッケージの説明を指定します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、パッケージの目的について記述することをお勧めします。  
  
 **移行先**  
 ターゲットを表示 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]またはファイル)、変換先ファイルの指定されていた。  
  
## <a name="target-dynamic-options"></a>保存先の動的オプション  
  
### <a name="target--sql-server"></a>[変換先] = [SQL Server]  
 **サーバー名**  
 保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択した場合は、保存先のサーバー名を入力または選択します。  
  
 **[Windows 認証を使用する]**  
 保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択した場合は、Windows 統合認証を使用してサーバーに接続するかどうかを指定します。 これは、推奨される認証方法です。  
  
 **[SQL Server 認証を使用する]**  
 選択した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換先、SQL Server 認証を使用して、サーバーに接続するかどうかを指定します。  
  
 **ユーザー名**  
 選択した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換先、および SQL Server 認証の種類を指定した、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー名。  
  
 **Password**  
 選択した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換先、および SQL Server 認証の種類を指定した、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パスワード。  
  
### <a name="target--file-system"></a>[変換先] = [ファイル システム]  
 **[ファイル名]**  
 ファイル変換先を選択すると、目的のファイルのパスを入力またはを使用して、**参照**ボタンをクリックします。  
  
 **[参照]**  
 使用して、変換先ファイルをファイル変換先を選択すると、参照、**パッケージの保存** ダイアログ ボックス。  
  
## <a name="see-also"></a>参照  
 [パッケージを保存する](../save-packages.md)  
  
  
