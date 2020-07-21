---
title: '[パッケージの保存および実行] (SQL Server インポートおよびエクスポートウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2bb7f32cc36b14682de4629b238883acde4a015a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436819"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a>[パッケージの保存および実行] (SQL Server インポートおよびエクスポート ウィザード)
  [**パッケージの保存と実行**] ダイアログボックスを使用すると、すぐにパッケージを実行したり、後で実行するように保存したり、その両方を実行したりできます。  
  
> [!NOTE]  
>  パッケージの実行が完了する前に停止した場合、[**保存**] チェックボックスをオンにした場合でも、パッケージは保存されません。  
  
 このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。 ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。  
  
 SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。 また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。 ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。 詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **直ちに実行**  
 このオプションを選択すると、すぐにパッケージを実行します。  
  
 **[SSIS パッケージの保存]**  
 パッケージをすぐに実行するためのオプションを使用して、パッケージを後で実行するために保存します。  
  
> [!NOTE]  
>  では、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] ウィザードによって作成されたパッケージを保存するオプションは使用できません。  
  
 **SQL Server**  
 パッケージをデータベースに保存するには、このオプションを選択し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` ます。  
  
> [!NOTE]  
>  このオプションは、[ **SSIS パッケージの保存**] オプションを選択した場合にのみ使用できます。  
  
 **ファイル システム**  
 このオプションを選択して、.dtsx 拡張子を持つファイルとしてパッケージを保存します。  
  
> [!NOTE]  
>  このオプションは、[ **SSIS パッケージの保存**] オプションを選択した場合にのみ使用できます。  
  
 **パッケージの保護レベル**  
 一覧から保護レベルを選択します。  
  
 保護レベルによって、パッケージ保護の方法、パスワードまたはユーザー キー、適用範囲が決定されます。 保護対象には、すべてのデータを含めることも機密データのみを含めることもできます。 パッケージのセキュリティの要件とオプションを理解するには、「パッケージとセキュリティの[概要 &#40;Integration Services&#41;](../security/security-overview-integration-services.md)の[機密データの Access Control](../security/access-control-for-sensitive-data-in-packages.md)を参照してください。  
  
> [!NOTE]  
>  このオプションは、[ **SSIS パッケージの保存**] オプションを選択した場合にのみ使用できます。  
  
 **パスワード**  
 パスワードを入力します。  
  
> [!NOTE]  
>  このオプションは、[**パッケージの保護レベル**] オプションで [**機微なデータをパスワードで暗号化**する] または [**すべてのデータをパスワードで暗号化**する] を設定した場合にのみ使用できます。  
  
 **[パスワードの再入力]**  
 パスワードを再度入力します。  
  
> [!NOTE]  
>  このオプションは、[**パッケージの保護レベル**] オプションで [**機微なデータをパスワードで暗号化**する] または [**すべてのデータをパスワードで暗号化**する] を設定した場合にのみ使用できます。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトとパッケージの実行](../packages/run-integration-services-ssis-packages.md)   
 [パッケージを保存する](../save-packages.md)  
  
  
