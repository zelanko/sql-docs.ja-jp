---
title: ポリシー ベースの管理ポリシーのインポート | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 54e0ca12595b0ce8bdde128c9261918c910ffdcf
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934349"
---
# <a name="import-a-policy-based-management-policy"></a>ポリシー ベースの管理ポリシーのインポート
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でポリシー ベースの管理ポリシー インスタンスをインポートする方法について説明します。  
  
## <a name="permissions"></a>アクセス許可
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。

  
##  <a name="using-sql-server-management-studio"></a>SQL Server Management Studio を使用する  
  
### <a name="to-import-a-policy-instance"></a>ポリシー インスタンスをインポートするには  
  
1.  **オブジェクト エクスプローラー**で、プラス記号をクリックして、新しくインポートするポリシー インスタンスを配置するサーバーを展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  プラス記号をクリックして **[ポリシー管理]** を展開します。  
  
4.  **[ポリシー]** フォルダーを右クリックし、 **[ポリシーのインポート]** をクリックします。  
  
5.  **[インポート]** ダイアログ ボックスで、ファイルのパスと名前を入力します。または、参照ボタン (**[...]**) を使用してポリシーを含んでいる XML ファイルを特定し、ファイルを選択します。 **[インポート]** ダイアログ ボックスで利用可能なオプションの詳細については、「 [Import Policies Dialog Box](../../relational-databases/policy-based-management/import-policies-dialog-box.md)」を参照してください。  
  
6.  完了したら、 **[OK]** をクリックします。  


## <a name="example-policies"></a>ポリシーの例
 ポリシーの例は [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]に含まれていませんが、以前に配布されたポリシーの例には、[SQL Server Management Studio v17](../../ssms/release-notes-ssms.md#previous-ssms-releases) をインストールすることによってアクセスできます。  SQL Server Management Studio v17 のインストールが完了すると、ポリシーの例は `C:\Program Files (x86)\Microsoft SQL Server\140\Tools\Policies` で見つけることができます。 これらのポリシーは、ご自分のポリシー ベースの管理ポリシーの基礎としてインポートおよび使用できます。
