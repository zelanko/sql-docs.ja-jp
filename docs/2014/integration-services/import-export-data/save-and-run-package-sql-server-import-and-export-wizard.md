---
title: 保存パッケージおよび実行 (SQL Server インポートおよびエクスポート ウィザード) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6071acee5eb7d888bdf4182a30f433e531754f64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083667"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a>[パッケージの保存および実行] (SQL Server インポートおよびエクスポート ウィザード)
  使用して、**パッケージの実行を保存して**パッケージを実行する、すぐに、後で、実行するにまたはその両方を保存 ダイアログ ボックス。  
  
> [!NOTE]  
>  実行が終了する前にパッケージを停止する場合、パッケージは保存されません、選択した場合でも、**保存**チェック ボックスをオンします。  
  
 このウィザードの詳細については、次を参照してください。 [SQL Server インポートおよびエクスポート ウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)です。 ウィザードを正常に実行するために必要なアクセス許可と同様に、ウィザードを開始するためのオプションの詳細については、次を参照してください。 [、SQL Server インポートおよびエクスポート ウィザードを実行](start-the-sql-server-import-and-export-wizard.md)です。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>および  
 **即時実行します。**  
 このオプションを選択すると、すぐにパッケージを実行します。  
  
 **SSIS パッケージの保存**  
 パッケージをすぐに実行するためのオプションを使用して、パッケージを後で実行するために保存します。  
  
> [!NOTE]  
>  [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]、ウィザードによって作成されたパッケージを保存するオプションは使用できません。  
  
 **SQL Server**  
 このオプションを選択して、パッケージを [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` データベースに保存します。  
  
> [!NOTE]  
>  このオプションは選択した場合にのみ使用可能な**SSIS パッケージの保存**オプション。  
  
 **ファイル システム**  
 このオプションを選択して、.dtsx 拡張子を持つファイルとしてパッケージを保存します。  
  
> [!NOTE]  
>  このオプションは選択した場合にのみ使用可能な**SSIS パッケージの保存**オプション。  
  
 **パッケージの保護レベル**  
 一覧から保護レベルを選択します。  
  
 保護レベルによって、パッケージ保護の方法、パスワードまたはユーザー キー、適用範囲が決定されます。 保護対象には、すべてのデータを含めることも機密データのみを含めることもできます。 要件とパッケージのセキュリティ オプションを理解するのを参照してください。[パッケージ内の機密データのアクセス制御](../security/access-control-for-sensitive-data-in-packages.md)と[セキュリティの概要&#40;Integration Services&#41;](../security/security-overview-integration-services.md)です。  
  
> [!NOTE]  
>  このオプションは選択した場合にのみ使用可能な**SSIS パッケージの保存**オプション。  
  
 **Password**  
 パスワードを入力します。  
  
> [!NOTE]  
>  このオプションは設定した場合にのみ使用可能な**パッケージの保護レベル**するいずれかのオプション**パスワードを使用して機密データを暗号化**または**パスワードを持つすべてのデータを暗号化**です。  
  
 **パスワードの再入力**  
 パスワードを再度入力します。  
  
> [!NOTE]  
>  このオプションは設定した場合にのみ使用可能な**パッケージの保護レベル**するいずれかのオプション**パスワードを使用して機密データを暗号化**または**パスワードを持つすべてのデータを暗号化**です。  
  
## <a name="see-also"></a>参照  
 [プロジェクトとパッケージの実行](../packages/run-integration-services-ssis-packages.md)   
 [パッケージを保存する](../save-packages.md)  
  
  