---
title: SQL Server への接続 (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: d73abd3a-80df-4293-b973-1723069db049
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 8dc64c84a8d14ea86893d52044894e0af2b1a3bb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103213"
---
# <a name="connect-to-sql-server-mysqltosql"></a>SQL Server への接続 (MySQLToSQL)
[ **SQL Server への接続**] ダイアログボックスを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に移行するのインスタンスに接続できます。 [ **SQL Server への接続**] ダイアログボックスにアクセスするには、[**ファイル**] メニューの [ **SQL Server に接続**] をクリックします。  
  
## <a name="options"></a>オプション  
**サーバー名**  
接続する SQL Server のインスタンスを入力または選択します。 既定では、最近接続したインスタンスが表示されます。  
  
-   ローカルコンピューター上の既定のインスタンスに接続している場合は、 **localhost**またはドット (**.**) のいずれかを入力できます。  
  
-   別のコンピューター上の既定のインスタンスに接続している場合は、コンピューターの名前を入力します。  
  
-   別のコンピューター上の名前付きインスタンスに接続する場合は、コンピューター名、円記号、インスタンス名 ( *MyServer*\\*myinstance*など) を入力します。  
  
**サーバーポート**  
の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスが既定のポート (1433) で接続を受け入れるように構成されていない場合は、ポート番号を入力します。 それ以外の場合は、この値を空白のままにします。  
  
**[データベース]**  
オブジェクトとデータを移行するデータベースを指定します。 このオプションは、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]再接続するときには使用できません。  
  
**認証**  
へ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の接続に使用する認証方法を選択します。 現在の Windows アカウントを使用するには、[Windows 認証] を選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインとパスワードを指定するには[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、[認証] を選択します。  
  
**ユーザー名**  
認証を使用し[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ている場合は、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスのログインを入力します。 Windows 認証を使用している場合、このオプションは使用できません。  
  
**パスワード**  
認証を使用し[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ている場合は、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスにログインするためのパスワードを入力します。 Windows 認証を使用している場合、このオプションは使用できません。  
  
**暗号化接続**  
SQL Server に安全に接続する場合は、[**暗号化接続**] チェックボックスをオンにして、暗号化接続を使用します。  
  
**サーバー証明書を信頼する**  
このオプションを使用する場合は、[**サーバー証明書を信頼**する] チェックボックスをオンにします。  
  
> [!NOTE]  
> 信頼された**サーバー証明書**を有効にするには、"Encrypt" を**True**に設定する必要があります。  
  
