---
title: 新規または編集サーバーの登録 ([全般] タブ) (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.reportserver.f1
ms.assetid: 5f899a8e-52ef-46b5-b7a9-f200ccd9f724
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a9892a6fb3033be549d95b708a012e55d40bcb80
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84930511"
---
# <a name="new-or-edit-server-registration-general-tab-reporting-services"></a>[新規サーバーの登録] または [サーバー登録プロパティの編集] ([全般] タブ) (Reporting Services)
  このタブを使用すると、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のインスタンスを登録するときのオプションを指定できます。  
  
 このページにアクセスするには、[登録済みサーバー] で、 **[登録済みサーバー]** ツール バーの **[Reporting Services]** をクリックし、登録済みサーバー グループ ( **[Reporting Services]** など) を右クリックして、 **[新規作成]** をポイントし、 **[サーバーの登録]** をクリックします。  
  
## <a name="options"></a>Options  
 **サーバーの種類**  
 サーバーが登録済みサーバーから登録されている場合、[**サーバーの種類**] ボックスは読み取り専用になり、[**登録済みサーバー** ] ペインに表示されているサーバーの種類と一致します。 別の種類のサーバーを登録するには、 **[登録済みサーバー]** ツール バーで目的のサーバーをクリックした後で、新しいサーバーの登録を開始します。  
  
 **サーバー名**  
 接続先のレポート サーバー インスタンスを指定します。 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]では、インスタンス名を使用してレポート サーバーにアクセスできます。 インストールする各 SQL Server インスタンスに対して、1 つのレポート サーバー インスタンスを使用できます。 既定のインスタンスを使用する場合は、SQL Server インスタンスの名前を入力します。 名前付きのインスタンスを使用する場合は、レポート サーバーに接続するための名前付きインスタンスを MSSQL$InstanceName の形式で指定します。  
  
 **認証**  
 レポート サーバーへの認証は、インターネット インフォメーション サービス (IIS) によって実行されます。 Reporting Services に接続する際に、次のいずれかの認証モードを選択します。  
  
 **Windows 認証モード ([Windows 認証])**  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 資格情報を使用して、レポート サーバー インスタンスに接続します。  
  
 **基本認証**  
 Reporting Services をインストールしたときに、基本認証を使用するように構成している場合は、 **基本認証** を使用して接続します。  
  
 **フォーム認証**  
 Reporting Services をインストールしたときに、カスタム認証拡張機能を使用するように構成している場合は、 **フォーム認証** を使用して接続します。  
  
 **ユーザー名**  
 接続に使用するログイン名を入力します。 このオプションは、 **[基本認証]** または **[フォーム認証]** を選択した場合にのみ使用できます。  
  
 **パスワード**  
 ユーザー名に対応するパスワードを入力します。 このオプションは、 **[基本認証]** または **[フォーム認証]** を選択した場合にのみ編集できます。  
  
 **パスワードを保存する**  
 入力したパスワードを保存します。 このオプションは、 **[基本認証]** または **[フォーム認証]** をクリックした場合にのみ使用できます。  
  
> [!NOTE]  
>   いったんパスワードを保存した後に、パスワードが保存されないようにするには、このチェック ボックスをオフにしてから **[保存]** をクリックします。  
  
 **[登録済みサーバーの名前]**  
 [登録済みサーバー] に表示する名前です。 この名前は、 **[サーバー名]** ボックスの名前と同じである必要はありません。  
  
 **[登録済みサーバーの説明]**  
 サーバーの説明をオプションで入力します。  
  
 **テスト**  
 クリックすると、 **[サーバー名]** で選択されたサーバーへの接続をテストします。  
  
 **保存**  
 クリックすると、登録済みサーバーの設定を保存します。  
  
  
