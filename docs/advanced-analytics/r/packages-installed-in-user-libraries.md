---
title: "ユーザー ライブラリにインストールされているパッケージ | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99ffd9b8-aa6d-4ac2-9840-4e66d0463978
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b4d5c7f3d1d0da5e1967140fcbdfcf60ba4571e7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="packages-installed-in-user-libraries"></a>ユーザー ライブラリにインストールされているパッケージ

新しい R パッケージを必要なユーザーが管理者でない場合は、パッケージを既定の場所にインストールすることはできません。この場合、既定では、パッケージはプライベートのユーザー ライブラリにインストールされます。 

一般的な R 開発環境でコード内のパッケージを参照するには、R 環境変数 `libPath` に場所を追加するか、次のようにパッケージの完全なパスを参照します。  
  
~~~~
library("c:/Users/<username>/R/win-library/packagename")  
~~~~

## <a name="problems-with-packages-in-user-libraries"></a>ユーザー ライブラリのパッケージに関する問題

ただし [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、この回避策はサポートされて**いません**。パッケージは既定のライブラリにインストールする必要があります。 パッケージが既定のライブラリにインストールされていない場合は、パッケージを呼び出したときに次のエラーが送信されることがあります。

*ライブラリ(xxx) でエラー: 'xxx' という名前のパッケージはありません*
 

このため、R ソリューションを移行して [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] で実行するには、次の手順を実行することが重要です。
+ 既定のライブラリに必要なすべてのパッケージをインストールします。
+ コードを編集して、パッケージがアドホック ディレクトリやユーザー ライブラリからではなく、既定のライブラリから読み込まれるようにします。
+ インストールされていないパッケージへの呼び出しがないよう、コードを確認します。
+ パッケージを動的にインストールしようとするコードを変更します。
 
パッケージが既定のライブラリにインストールされていると、R コードで別のライブラリが指定されている場合でも、R ランタイムは既定のライブラリからパッケージを読み込みます。

## <a name="see-also"></a>参照
