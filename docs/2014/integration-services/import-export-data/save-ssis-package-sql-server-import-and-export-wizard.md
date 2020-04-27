---
title: '[SSIS パッケージの保存] (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6af26cafd4f8dd9bf874ae7860c4f796bef48ae1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62892767"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>[SSIS パッケージの保存]\(SQL Server インポートおよびエクスポート ウィザード)
  [ **SSIS パッケージの保存**] ページを使用する[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と、Integration Services[!INCLUDE[ssIS](../../includes/ssis-md.md)]() パッケージ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb`の名前を指定し、データベースまたは拡張子が .dtsx のファイルに保存できます。  
  
> [!NOTE]  
>  で[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]は、ウィザードによって作成されたパッケージを保存するオプションは使用できません。  
  
 このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。 ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **名前**  
 パッケージの一意な名前を指定します。  
  
 **説明**  
 パッケージの説明を指定します。 パッケージを自己文書化して目的を明確にし、保守が容易になるように、パッケージの目的について記述することをお勧めします。  
  
 **移行先**  
 保存先ファイルとしてあらかじめ指定されているターゲット ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] またはファイル) を表示します。  
  
## <a name="target-dynamic-options"></a>保存先の動的オプション  
  
### <a name="target--sql-server"></a>[変換先] = [SQL Server]  
 **サーバー名**  
 保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択した場合は、保存先のサーバー名を入力または選択します。  
  
 **Windows 認証を使用する**  
 保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択した場合は、Windows 統合認証を使用してサーバーに接続するかどうかを指定します。 これは、推奨される認証方法です。  
  
 **SQL Server 認証を使用する**  
 保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択した場合は、SQL Server 認証を使用してサーバーに接続するかどうかを指定します。  
  
 **ユーザー名**  
 保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択し、SQL Server 認証を使用してサーバーに接続することを指定した場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のユーザー名を入力します。  
  
 **パスワード**  
 保存先として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を選択し、SQL Server 認証を使用してサーバーに接続することを指定した場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパスワードを入力します。  
  
### <a name="target--file-system"></a>[変換先] = [ファイル システム]  
 **[ファイル名]**  
 ファイルの保存先を選択した場合は、変換先ファイルのパスを入力するか、[**参照**] ボタンを使用します。  
  
 **参照**  
 ファイルの保存先を選択したら、[**パッケージの保存**] ダイアログボックスを使用して目的のファイルを参照します。  
  
## <a name="see-also"></a>参照  
 [パッケージを保存する](../save-packages.md)  
  
  
