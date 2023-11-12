


# ステップ１

## テーブル設計をしてください


```
CREATE TABLE Channel (
    ChannelID INT PRIMARY KEY AUTO_INCREMENT,
    ChannelName VARCHAR(255) not null UNIQUE
);
```

```
CREATE TABLE Program (
    ChannelID INT not null,
    Date DATE not null,
    TimeSlot TIME not null,
    EpisodeID INT not null,
    Viewers INT DEFAULT 0,
    PRIMARY KEY (ChannelID, Date, TimeSlot),
    FOREIGN KEY (ChannelID) REFERENCES Channel(ChannelID)
);
```

```
CREATE TABLE ProgramDetail (
    ProgramID INT PRIMARY KEY AUTO_INCREMENT,
    ProgramName VARCHAR(255) not null unique,
    ProgramDetail TEXT not null
);
```


```
CREATE TABLE Genre (
    ProgramID INT,
    Genre VARCHAR(255)  not null,
    FOREIGN KEY (ProgramID) REFERENCES ProgramDetail(ProgramID)
);
```

```
CREATE TABLE Episode (
    EpisodeID INT PRIMARY KEY auto_increment,
    SeasonNumber INT,
    EpisodeNumber INT,
    ProgramID INT,
    EpisodeName VARCHAR(255) NOT NULL,
    Details TEXT not null,
    Duration TIME NOT NULL,
    ReleaseDate DATE NOT NULL,
    Viewers INT DEFAULT 0,
    FOREIGN KEY (ProgramID) REFERENCES ProgramDetail(ProgramID)
);
```


```
drop table Program;
```

```
CREATE TABLE Program (
    ChannelID INT not null,
    Date DATE not null,
    TimeSlot TIME not null,
    EpisodeID INT not null,
    Viewers INT DEFAULT 0,
    PRIMARY KEY (ChannelID, Date, TimeSlot),
    FOREIGN KEY (ChannelID) REFERENCES Channel(ChannelID),
    FOREIGN KEY (EpisodeID) REFERENCES Episode(EpisodeID)
);
```

# ステップ２

## サンプルデータ格納

### 1.データベースを構築します

```
create database apdata;
use apdata;
```

### 2.ステップ1で設計したテーブルを構築します

```
CREATE TABLE Channel (
    ChannelID INT PRIMARY KEY AUTO_INCREMENT,
    ChannelName VARCHAR(255) not null UNIQUE
);
```

```
CREATE TABLE Program (
    ChannelID INT not null,
    Date DATE not null,
    TimeSlot TIME not null,
    EpisodeID INT not null,
    Viewers INT DEFAULT 0,
    PRIMARY KEY (ChannelID, Date, TimeSlot),
    FOREIGN KEY (ChannelID) REFERENCES Channel(ChannelID)
);
```

```
CREATE TABLE ProgramDetail (
    ProgramID INT PRIMARY KEY AUTO_INCREMENT,
    ProgramName VARCHAR(255) not null unique,
    ProgramDetail TEXT not null
);
```


```
CREATE TABLE Genre (
    ProgramID INT,
    Genre VARCHAR(255)  not null,
    FOREIGN KEY (ProgramID) REFERENCES ProgramDetail(ProgramID)
);
```

```
CREATE TABLE Episode (
    EpisodeID INT PRIMARY KEY auto_increment,
    SeasonNumber INT,
    EpisodeNumber INT,
    ProgramID INT,
    EpisodeName VARCHAR(255) NOT NULL,
    Details TEXT not null,
    Duration TIME NOT NULL,
    ReleaseDate DATE NOT NULL,
    Viewers INT DEFAULT 0,
    FOREIGN KEY (ProgramID) REFERENCES ProgramDetail(ProgramID)
);
```


```
drop table Program;
```

```
CREATE TABLE Program (
    ChannelID INT not null,
    Date DATE not null,
    TimeSlot TIME not null,
    EpisodeID INT not null,
    Viewers INT DEFAULT 0,
    PRIMARY KEY (ChannelID, Date, TimeSlot),
    FOREIGN KEY (ChannelID) REFERENCES Channel(ChannelID),
    FOREIGN KEY (EpisodeID) REFERENCES Episode(EpisodeID)
);
```

### 3.サンプルデータの挿入

```
INSERT INTO Channel (ChannelID, ChannelName) VALUES (01,’ニュース’);
INSERT INTO Channel (ChannelID, ChannelName) VALUES (02,’ドラマ’);
INSERT INTO Channel (ChannelID, ChannelName) VALUES (03’映画’);
INSERT INTO Channel (ChannelID, ChannelName) VALUES (04’スポーツ’);
INSERT INTO Channel (ChannelID, ChannelName) VALUES (05,’アニメ’);
```

```
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (001,鬼滅の刃’, ‘鬼滅の刃’という番組);
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (2,'ドラゴンボール', 'ドラゴンボールという番組');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (3,'バスケットボールの試合', 'バスケの試合');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (4,'サッカーの試合', 'サッカーの試合');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (5,'野球試合', '野球の試合');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (6,'ワンピース', 'ワンピースという番組');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (7,'のど自慢大会', 'のど自慢大会という番組');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (8,'カラオケバトル', 'カラオケバトルという番組');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (9,'貞子', '貞子という映画');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (10,'世田谷殺人事件', '世田谷殺人事件というニュース');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (11,'練馬強盗事件', '練馬強盗事件というニュース');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (12,'名探偵コナン', '名探偵コナンという映画');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (13,'ジョーカー', 'ジョーカーという映画');
INSERT INTO ProgramDetail (ProgramID,ProgramName, ProgramDetail) VALUES (14,'ラッキーセブン', 'ラッキーセブンというドラマ');
```

```
INSERT INTO Genre (Genre, ProgramID) VALUES (‘アニメ’, 1);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘アニメ’, 2);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘スポーツ’, 3);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘スポーツ’, 4);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘スポーツ’, 5);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘アニメ’, 6);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘音楽’, 7);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘ホラー’, 8);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘ニュース’, 9);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘ニュース’, 10);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘邦画’, 11);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘洋画’, 12);
INSERT INTO Genre (Genre, ProgramID) VALUES (‘ドラマ’, 13);
```

```
INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (1,1, 1, 1, '鬼滅の刃 1話', '鬼滅の刃１話', '02:00:00', '2023-01-01', 1000);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (2,1, 2, 1, '鬼滅の刃 ２話', '鬼滅の刃', '02:00:00', '2023-01-02', 2000);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (3,1, 3, 1, '鬼滅の刃 ３話', '鬼滅の刃', '02:00:00', '2023-01-03', 2300);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (19,null, null, 3, 'バスケットボール試合', 'ジョーダン対マイク', '02:00:00', '2023-01-01', 800);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (20,null, null, 4, 'サッカー試合', '日本対フランス', '02:00:00', '2023-01-02', 700);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (21,null, null, 5, '野球試合', 'ヤクルト対ソフトバンク', '02:00:00', '2023-01-03', 300);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (38,null, null, 12, '名探偵コナン', '黒の組織編', '02:00:00', '2023-01-06', 3020);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (39,null, null, 13, 'ジョーカー', '海外編', '02:00:00', '2023-01-06', 2000);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (40,1, 1, 14, 'ラッキーセブン　１話', 'ラッキーセブン', '02:00:00', '2023-01-09', 700);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (41,1, 2, 14, 'ラッキーセブン　２話', 'ラッキーセブン', '02:00:00', '2023-01-10', 6000);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (42,1, 3, 14, 'ラッキーセブン　３話', 'ラッキーセブン', '02:00:00', '2023-01-10', 500);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (36,null, null, 10, '世田谷殺人事件', '悲しい事件が起きました', '02:00:00', '2023-01-06', 3020);

INSERT INTO Episode (EpisodeID,SeasonNumber, EpisodeNumber, ProgramID, EpisodeName, Details, Duration, ReleaseDate, Viewers) 
VALUES (37,null, null, 11, '練馬強盗事件', '少し悲しい事件', '02:00:00', '2023-01-06', 2000);
```



```
INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (1, '2023-01-06', '07:00:00', 36, 500);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (1, '2023-01-06', '09:00:00', 37, 400);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (2, '2023-01-09', '07:00:00', 40, 400);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (2, '2023-01-10', '09:00:00', 41, 30);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (2, '2023-01-10', '11:00:00', 42, 400);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (3, '2023-01-06', '11:00:00', 38, 200);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (3, '2023-01-06', '13:00:00', 39, 300);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (4, '2023-01-01', '07:00:00', 19, 600);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (4, '2023-01-02', '07:00:00', 20, 500);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (4, '2023-01-03', '07:00:00', 21, 600);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (5, '2023-01-01', '09:00:00', 1, 400);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (5, '2023-01-02', '09:00:00', 2, 400);

INSERT INTO Program (ChannelID, Date, TimeSlot, EpisodeID, Viewers) 
VALUES (5, '2023-01-03', '09:00:00', 3, 300);
```



# ステップ3

## データ抽出クエリ

1. よく見られているエピソードを知りたいです。エピソード視聴数トップ3のエピソードタイトルと視聴数を取得してください 

```
SELECT EpisodeName, Viewers
FROM Episode
ORDER BY Viewers DESC
LIMIT 3;
```


2. よく見られているエピソードの番組情報やシーズン情報も合わせて知りたいです。エピソード視聴数トップ3の番組タイトル、シーズン数、エピソード数、エピソードタイトル、視聴数を取得してください 

```
SELECT EpisodeName,SeasonNumber,EpisodeNumber, Viewers 
FROM Episode 
ORDER BY Viewers DESC 
LIMIT 3;
```

3.本日の番組表を表示するために、本日、どのチャンネルの、何時から、何の番組が放送されるのかを知りたいです。本日放送される全ての番組に対して、チャンネル名、放送開始時刻(日付+時間)、放送終了時刻、シーズン数、エピソード数、エピソードタイトル、エピソード詳細を取得してください。なお、番組の開始時刻が本日のものを本日方法される番組とみなすものとします 

```
SELECT
    c.ChannelName,
    p.TimeSlot AS StartTime,
    CONCAT(p.Date, ' ', p.TimeSlot) AS StartTime,
    DATE_ADD(p.TimeSlot, INTERVAL COALESCE(e.Duration, 0) HOUR) AS EndTime,
    e.SeasonNumber,
    e.EpisodeNumber,
    e.EpisodeName,
    e.Details
FROM
    Program p
JOIN
    Channel c ON p.ChannelID = c.ChannelID
JOIN
    Episode e ON p.EpisodeID = e.EpisodeID
WHERE
    DATE(e.ReleaseDate) = '2023-11-13';
```



4.ドラマというチャンネルがあったとして、ドラマのチャンネルの番組表を表示するために、本日から一週間分、何日の何時から何の番組が放送されるのかを知りたいです。ドラマのチャンネルに対して、放送開始時刻、放送終了時刻、シーズン数、エピソード数、エピソードタイトル、エピソード詳細を本日から一週間分取得してください 

```
SELECT
    c.ChannelName,
    p.TimeSlot AS StartTime,
    CONCAT(p.Date, ' ', p.TimeSlot) AS StartTime,
    DATE_ADD(p.TimeSlot, INTERVAL COALESCE(e.Duration, 0) HOUR) AS EndTime,
    e.SeasonNumber,
    e.EpisodeNumber,
    e.EpisodeName,
    e.Details
FROM
    Program p
JOIN
    Channel c ON p.ChannelID = c.ChannelID
JOIN
    Episode e ON p.EpisodeID = e.EpisodeID
WHERE
    DATE(e.ReleaseDate) BETWEEN '2023-01-01' AND '2023-01-07' && c.ChannelName = 'ドラマ';
```


*今後、advancedとRuby改善にも早急に取り掛かります。*







