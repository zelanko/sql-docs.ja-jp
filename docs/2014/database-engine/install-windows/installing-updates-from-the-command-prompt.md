---
title: コマンド プロンプトからの更新プログラムのインストール | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: bc98ba2b-aae9-4d01-aa85-d4c36428cb0b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3be1cf08e3e3ac2278bfbf249c3310b179a9cf6c
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84932263"
---
# <a name="installing-updates-from-the-command-prompt"></a>コマンド プロンプトからの更新プログラムのインストール
  インストール スクリプトをテストし、必要に応じて変更してください。  
  
## <a name="sample-syntax-for-installation"></a>インストールのサンプル構文  
 更新プログラム パッケージの名前はさまざまであり、言語、エディション、およびプロセッサ コンポーネントが含まれる場合があります。 コマンド プロンプトで更新プログラムを適用する際に、<package_name> の部分は実際の更新プログラム パッケージの名前に置き換えてください。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 1 つのインスタンスと、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や管理ツールなどのすべての共有コンポーネントを更新します。インスタンスを指定するには、InstanceName パラメーターまたは InstanceID パラメーターを使用します。 準備済みインスタンスを更新するには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、InstanceID パラメーター<package_name # C1.exe/qs/IAcceptSQLServerLicenseTerms/Action = patch/InstanceName = MyInstance または <package_name # C3.exe/qs/IAcceptSQLServerLicenseTerms/Action = patch/instanceid = を指定する必要があり \<Instance ID> ます。  
  
-   セットアップでは、メインの製品と使用可能な更新プログラムが同時にインストールされるように、最新の製品の更新プログラムとメインの製品のインストールを統合できます。 製品の更新プログラムを含めるようにデータベースエンジンインスタンスのインストールを準備するには、setup.exe/q/IAcceptSQLServerLicenseTerms/ACTION = PrepareImage/updateenabled = True/updateenabled = True/updatesource = \<path where the update is downloaded> /INSTANCEID = \<Instance ID> /FEATURES = sqlengine を使用します。  
  
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
  
|Switch|説明|  
|------------|-----------------|  
|**/?**|自動インストールのコマンド プロンプト ヘルプを表示します。|  
|**/action=Patch または /action=RemovePatch**|インストール動作 (Patch または RemovePatch) を指定します。|  
|**/allinstances**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを、すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント (共有、インスタンス非対応) に適用します。|  
|**/instancename = instancename** <sup>1</sup>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを、InstanceName という名前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント (共有、インスタンス非対応) に適用します。|  
|**/InstanceID=Inst1**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムを、Inst1 という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント (共有、インスタンス非対応) に適用します。|  
|**/quiet**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新プログラムのセットアップを自動モードで実行します。|  
|**/qs**|進行状況 UI ダイアログのみを表示します。|  
|**/UpdateEnabled**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップが製品の更新プログラムを検出し、それらを含める必要があるかどうかを指定します。 有効値は True および False または 1 および 0 です。 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップには検出された更新プログラムが含まれます。|  
|**/IAcceptSQLServerLicenseTerms**|自動インストールのために /Q パラメーターまたは /QS パラメーターを指定した場合にのみ必須です。|  
  
 <sup>1</sup>このパラメーターを指定して、の準備済みインスタンスに更新プログラムを適用することはできません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 代わりに /instanceID パラメーターを指定してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server サービスのインストールの概要](../../sql-server/install/overview-of-sql-server-servicing-installation.md)  
  
  
