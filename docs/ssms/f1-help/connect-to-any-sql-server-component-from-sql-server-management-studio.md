---
title: SSMS から SQL Server コンポーネントへの接続 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-f1
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 58bd639a16003fe718a226b1aea7a3bb3bf5b470
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33042459"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a>SQL Server Management Studio から SQL Server コンポーネントへの接続
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]の各コンポーネントを管理する機能があります。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] を使用して、以下のコンポーネントに接続します。  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンス。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)]の各コンポーネントを管理する機能があります。  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)]の各コンポーネントを管理する機能があります。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)]の各コンポーネントを管理する機能があります。  
  
[!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] では、データ ソースへの接続を確立していなくてもクエリの編集は行えますが、他のほとんどのタスクの場合には接続が必要です。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] では **[サーバーへの接続]** ダイアログ ボックスを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] コンポーネントへの接続プロパティを設定できます。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] の起動時には **[サーバーへの接続]** ダイアログ ボックスが表示され、サーバーへの接続を求められます。 **[サーバーへの接続]** ダイアログ ボックスには最後に使用したときの接続設定が保持されます。  
  
> [!NOTE]  
> この機能をオフにして、接続を自動的に開始しないようにすることもできます。 詳細については、「 [データベース エンジン サービスのスタートアップ オプション](http://msdn.microsoft.com/en-us/d373298b-f6cf-458a-849d-7083ecb54ef5)」を参照してください。  
  
## <a name="saving-connections"></a>接続の保存  
登録済みサーバーで特定のサーバーへの接続を保存することや、ソリューション エクスプローラーでプロジェクトの接続を保存することができます。  
  
### <a name="saving-connections-in-registered-servers"></a>登録済みサーバーでの接続の保存  
サーバーを登録すると、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] によって [登録済みサーバー] に接続情報が保存されます。 登録済みサーバーに接続するには、[登録済みサーバー] 内のサーバー名をダブルクリックします。 サーバーへの接続が行われ、オブジェクト エクスプローラーにそのサーバーが表示されます。  
  
### <a name="saving-connections-in-solution-explorer"></a>ソリューション エクスプローラーでの接続の保存  
ソリューション エクスプローラーでは、プロジェクト内に、関連するクエリ、スクリプト、接続、その他の関連情報を格納することができます。 スクリプト プロジェクトには **[接続]** というノードがあり、ここに 1 つ以上の接続を保存できます。 接続を追加するには、 **[接続]** を右クリックして、 **[新しい接続]** をクリックします。 保存した接続にアクセスするには、 **[接続]** を展開して対象の接続をダブルクリックします。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] によって、その接続に関連付けられたクエリ ウィンドウが開かれます。 スクリプトを保存すると、そのスクリプトには特定の接続との関連が保持されます。  
  
## <a name="see-also"></a>参照  
[SQL Server Management Studio の使用 [SQL Server]](../../ssms/use-sql-server-management-studio.md)  
[オブジェクト エクスプローラー](../../ssms/object/object-explorer.md)  
  
