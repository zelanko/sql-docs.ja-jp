---
title: クラス ファイルから Java jar ファイルを作成する
description: クラス ファイルから Java jar ファイルを作成する方法について説明します。
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a105dde9046167257a86705f678466872785b4be
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85735093"
---
# <a name="create-a-java-jar-file-from-class-files"></a>クラス ファイルから Java jar ファイルを作成する
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

[SQL Server 言語拡張](../language-extensions-overview.md)を使用して Java コードを実行するとき、クラス ファイルを jar ファイルにパッケージ化する方法について説明します。 ファイルをパッケージ化することをお勧めします。

## <a name="create-a-jar-file"></a>jar ファイルを作成する

クラス ファイルから jar を作成するには、クラス ファイルが格納されているフォルダーに移動し、次のコマンドを実行します。

```cmd
jar -cf <MyJar.jar> *.class
```

`jar.exe` のパスがシステム パス変数の一部であることを確認します。 または、JDK フォルダーの `/bin` 以下にある jar の完全なパスを指定します。 次に例を示します。

```cmd
C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class
```

## <a name="next-steps"></a>次のステップ

+ [SQL Server 言語拡張で Java ランタイムを呼び出す方法](../how-to/call-java-from-sql.md)