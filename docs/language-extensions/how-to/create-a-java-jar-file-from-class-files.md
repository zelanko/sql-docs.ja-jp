---
title: クラス ファイルから Java jar ファイルを作成する
titleSuffix: SQL Server Language Extensions
description: クラス ファイルから Java jar ファイルを作成する方法について説明します。
author: dphansen
ms.author: davidph
ms.date: 07/25/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4cec311a28f9d5119b5a0aeb696597e8b34ba25a
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "73588776"
---
# <a name="create-a-java-jar-file-from-class-files"></a>クラス ファイルから Java jar ファイルを作成する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[SQL Server 言語拡張](../language-extensions-overview.md)を使用して Java コードを実行する場合は、クラス ファイルを jar ファイルにパッケージ化することをお勧めします。

## <a name="create-a-jar-file"></a>jar ファイルを作成する

クラス ファイルから jar を作成するには、クラス ファイルが格納されているフォルダーに移動し、次のコマンドを実行します。

```cmd
jar -cf <MyJar.jar> *.class
```

`jar.exe` のパスがシステム パス変数の一部であることを確認します。 または、JDK フォルダーの `/bin` 以下にある jar の完全なパスを指定します。 例:

```cmd
C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class
```

## <a name="next-steps"></a>次の手順

+ [SQL Server で Java を呼び出す方法](../how-to/call-java-from-sql.md)