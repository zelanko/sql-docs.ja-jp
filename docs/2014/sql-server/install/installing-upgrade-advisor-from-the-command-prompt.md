---
title: コマンド プロンプトからアップグレード アドバイザーをインストールする |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Upgrade Advisor
- command prompt [Upgrade Advisor]
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: a6841cc2-ca13-4b1c-9343-9e4d54312c3a
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8433aa58002095568a79013ec398f96f87abd22b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165977"
---
# <a name="installing-upgrade-advisor-from-the-command-prompt"></a>コマンド プロンプトからのアップグレード アドバイザーのインストール
  アップグレード アドバイザーをインストールするには、セットアップ ウィザードを使用する方法と、コマンド プロンプトを使用する方法があります。 コマンド プロンプトを使用すると、自動インストールを実行できます。  
  
## <a name="installation-syntax"></a>インストールの構文  
 コマンド プロンプトからのアップグレード アドバイザーのインストールに使用する基本構文は、次のとおりです。  
  
 `SQLUA.msi [options]`  
  
 次の表では、最も一般的なオプションを示します。  
  
|引数|説明|  
|--------------|-----------------|  
|/q [n&#124;b&#124;r&#124;f]|ユーザー インターフェイス (UI) レベルの設定:<br /><br /> n = UI なし<br /><br /> b = 基本 UI (進行状況のみ、プロンプトなし)<br /><br /> r = 一部 UI (インストール終了時のダイアログ ボックス)<br /><br /> f = 完全 UI|  
|/L|ログ ファイル オプションを指定します。 すべてのメッセージをログに記録する*log_file_name*を使用して **-l\*v * * * log_file_name*です。 エラー メッセージのみを記録する使用`-Le` *log_file_name*です。|  
|ADDLOCAL = ALL&AMP;#124;削除 = ALL&AMP;#124;REINSTALL = ALL|アップグレード アドバイザーのインストール (ADDLOCAL)、削除 (REMOVE)、または再インストール (REINSTALL) を実行するように指定します。|  
|UAINSTALLDIR=path|アップグレード アドバイザーをパスで指定した場所にインストールします。|  
  
## <a name="installation-examples"></a>インストール例  
 次の例は、コマンド プロンプトを使用してアップグレード アドバイザーをインストールする方法を示します。  
  
```  
SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 このコマンドの実行時に、Msiexec プログラムを使用することもできます。  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 これは、追加インストール オプションを使用する必要がある場合に役立ちます。  
  
## <a name="removal-examples"></a>削除例  
 次の例は、コマンド プロンプトを使用してアップグレード アドバイザーを削除する方法を示します。  
  
```  
SQLUA.msi /qn REMOVE=ALL  
```  
  
 このコマンドの実行時に、Msiexec プログラムを使用することもできます。  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn REMOVE=ALL  
```  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーをインストールします。](../../../2014/sql-server/install/installing-upgrade-advisor.md)   
 [アップグレード アドバイザーの前提条件](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  