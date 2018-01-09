---
title: "コマンドライン管理ツール: SqlLocalDB.exe |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apilocation: sqluserinstance.dll
ms.assetid: dd0882b1-a8a9-447a-8bdf-0f9d7f36d336
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6ffc8033651fedbe906086f0a35ef31d463f6e31
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="command-line-management-tool-sqllocaldbexe"></a>コマンド ライン管理ツール: SqlLocalDB.exe
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]SqlLocalDB.exe は、単純なツールをコマンドラインから LocalDB インスタンスを簡単に管理するユーザーを有効にします。 LocalDB インスタンスの API の単純なラッパーとして実装されています。 SQLCMD などの多くの SQL Server ツールの場合と同様、パラメーターはコマンド ライン引数として SqlLocalDB に渡され、出力はコンソールに送られます。  
  
 SqlLocalDB では、開発者が LocalDB を使用できます。API を呼び出すコードを記述したり、他のツールを使用したりする必要はありません。  
  
## <a name="sqllocaldb-options"></a>SqlLocalDB オプション  
 SqlLocalDB では、次のオプションがサポートされています。  
  
|オプション|実行内容|  
|------------|------------------|  
|`-?`|ヘルプ テキストを出力します。|  
|' create\|c「インスタンス名」[バージョン番号] [-s]'|指定された名前とバージョンで LocalDB インスタンスを新規作成します。<br /><br /> [version-number] パラメーターを省略した場合、既定で SqlLocalDB ビルド バージョンになります。<br /><br /> -s は、LocalDB インスタンスの新規作成後に、そのインスタンスを起動します。|  
|' delete\|d「のインスタンス名」'|指定した名前の LocalDB インスタンスを削除します。|  
|' スタートアップ|「インスタンス名」s'|指定した名前の LocalDB インスタンスを起動します。|  
|' stop\|「インスタンス名」p [-i\|-k]'|現在のクエリの実行が終了した後、指定した名前の LocalDB インスタンスを停止します。<br /><br /> -i は、NOWAIT オプション付きで LocalDB インスタンスのシャットダウンを要求します。<br /><br /> -k は、LocalDB インスタンス プロセスに通知することなく、そのプロセスを停止します。|  
|' share\|h [「所有者の SID またはアカウント」]「プライベート""共有名」'|指定された共有名を使用して、指定されたプライベート インスタンスを共有します。 ユーザー SID またはアカウント名を省略した場合、既定で現在のユーザーになります。|  
|' unshare\|u「共有名」'|指定された共有 LocalDB インスタンスの共有を解除します。|  
|' info\|しました '|現在のユーザーが所有している既存のすべての LocalDB インスタンス、および共有されているすべての LocalDB インスタンスを一覧表示します。|  
|' info\|「インスタンス名」i'|指定された LocalDB インスタンスに関する情報を出力します。|  
|' versions\|v'|コンピューターにインストールされているすべての LocalDB バージョンを一覧表示します。|  
|||  
|' trace\|t 先|オフ '|トレースのオンとオフを切り替えます。|  
  
 SqlLocalDB では、スペースを区切り文字として扱います。スペースと特殊文字が含まれるインスタンス名は、引用符で囲む必要があります。 例 :  
  
 `SqlLocalDB create "My instance name with spaces"`  
  
  
