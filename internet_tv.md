


## ステップ１

### テーブル設計をしてください


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


