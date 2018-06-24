---
title: コマンド プロンプトからの更新プログラムのインストール | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc98ba2b-aae9-4d01-aa85-d4c36428cb0b
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5d1fb09edce06159c748be8393f8cbd46e0397b7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073817"
---
# <a name="installing-updates-from-the-command-prompt"></a>コマンド プロンプトからの更新プログラムのインストール
  インストール スクリプトをテストし、必要に応じて変更してください。  
  
## <a name="sample-syntax-for-installation"></a>インストールのサンプル構文  
 更新プログラム パッケージの名前はさまざまであり、言語、エディション、およびプロセッサ コンポーネントが含まれる場合があります。 コマンド プロンプトで更新プログラムを適用する際に、<package_name> の部分は実際の更新プログラム パッケージの名前に置き換えてください。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのインスタンスと、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や管理ツールなどのすべての共有コンポーネントを更新します。インスタンスを指定するには、InstanceName パラメーターまたは InstanceID パラメーターを使用します。 準備済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを更新するには、InstanceID パラメーターに、<package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance または <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceID=\<インスタンス ID> を指定する必要があります。  
  
-   セットアップでは、メインの製品と使用可能な更新プログラムが同時にインストールされるように、最新の製品の更新プログラムとメインの製品のインストールを統合できます。 製品の更新プログラムが含まれるデータベース エンジン インスタンスのインストールを準備するには、setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=PrepareImage /UpdateEnabled=True /UpdateEnabled=True /UpdateSource=\<更新プログラムがダウンロードされたパス> /INSTANCEID=\<インスタンス ID> /FEATURES=SQLEngine を実行します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] や管理ツールなどの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 共有コンポーネントのみを更新するには、<package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch を実行します。  
  
-   コンピューター上のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスと、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や管理ツールなどのすべての共有コンポーネントを更新するには、<package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances を実行します。  
  
 コマンド プロンプトで更新プログラムを削除する際に、<package_name> の部分は実際の更新プログラム パッケージの名前に置き換えてください。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのインスタンスと、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や管理ツールなどのすべての共有コンポーネントから更新プログラムを削除するには、<package_name>.exe /qs /Action=RemovePatch /InstanceName=MyInstance を実行します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] や管理ツールなどの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 共有コンポーネントのみから更新プログラムを削除するには、<package_name>.exe /qs /Action=RemovePatch を実行します。  
  
    > [!NOTE]  
    >  更新プログラムのインストーラーによって、共有コンポーネントが常に最上位レベルのインスタンスのバージョンと同じかまたはそれ以上であることが保証されます。  
  
## <a name="supported-command-prompt-parameters"></a>サポートされているコマンド プロンプト パラメーター  
  
> [!IMPORTANT]  
>  セキュリティ資格情報は、できるだけ実行時に入力してください。 資格情報をスクリプト ファイルに含める必要がある場合は、不正なアクセスが行われないようにファイルをセキュリティで保護してください。  
  
|スイッチ|説明|  
|------------|-----------------|  
|**/?**|自動インストールのコマンド プロンプト ヘルプを表示します。|  
|**/action=Patch または /action=RemovePatch**|インストール動作 (Patch または RemovePatch) を指定します。|  
|**/allinstances**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを、すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント (共有、インスタンス非対応) に適用します。|  
|**/instancename = InstanceName** <sup>1</sup>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを、InstanceName という名前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント (共有、インスタンス非対応) に適用します。|  
|**/InstanceID=Inst1**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを、Inst1 という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント (共有、インスタンス非対応) に適用します。|  
|**/quiet**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムのセットアップを自動モードで実行します。|  
|**/qs**|進行状況 UI ダイアログのみを表示します。|  
|**/UpdateEnabled**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップが製品の更新プログラムを検出し、それらを含める必要があるかどうかを指定します。 有効値は True および False または 1 および 0 です。 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップには検出された更新プログラムが含まれます。|  
|**/IAcceptSQLServerLicenseTerms**|自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。|  
  
 <sup>1</sup>の準備済みインスタンスに更新プログラムを適用するには、このパラメーターを指定することはできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 代わりに /instanceID パラメーターを指定してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server サービスのインストールの概要](../../sql-server/install/overview-of-sql-server-servicing-installation.md)  
  
  