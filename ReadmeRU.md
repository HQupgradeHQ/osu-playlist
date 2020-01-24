# osu-playlist
Извлекает все осу треки, коллекции, регулярные выражения по тегам из .osu файла. Экспорт треков в директорию или в отдельный m3u8 плейлист 
# Использование
Переместите этот файл в папку osu!/Songs 
## Команды
### Экспорт треков в директорию или в отдельный m3u8 плейлист ,может занять некоторое время
  `python3 osu_playlist.py`
### Экспорт коллекции.Может быть с опечатками или с верхним или нижним регистром   
  `python3 osu_playlist.py --collection "название коллекции"` 
### регулярное выражине по тэгам из .osu файлов
  `python3 osu_playlist.py --regtag "regex"`
### обратное регулярное выражение (необязательно)
  `python3 osu_playlist.py -r "regex" -i `
### указать путь для экспорта аудио (необязательно)
 `python3 osu_playlist.py --to_dir "path"` 
### команды 
 `python3 osu_playlist.py --help` 

## Пример с  [mpv](https://mpv.io/):
  `mpv --playlist=playlist.m3u8 --shuffle --volume 35` 
## Пример  обратный поиск с регулярным выражением и экспорт в директорию
 `python3 osu_playlist.py -r "(azer|step)" -i -d "E:/music/osu_playlist"`

`-r "(azer|step)"` найдёт все треки с тэгами azer или step

`-i` (optional) вернёт обратное, все треки БЕЗ azer или step

`-d` (optional) экспорт .mp3 в директорию  E:/music/osu_playlist
 
# Использование osu_playlist.py как модуля
```python
import osu_playlist
from osu_playlist import osudict, names, namedict

print(len(names))
# это отфильтрует строки тегов, соответствующие azer или step 
first_search = osu_playlist.filter_tags(osudict, regtag="(azer|step") 
print(first_search)
# это отфильтрует строки тегов c first_search, соответствующие drumstep 
second_search = osu_playlist.filter_tags(
    osudict, regtag="drumstep", list_of_song_names=first_search
)
print(second_search)
# экспорт файлов мп3 
osu_playlist.export_to_dir(second_search)
```

# Pull requests
Pull requests относительно вещей прямо не связанных с программой не будут приняты 
Например, pull requests относительно README не будут приняты, вместо этого можете открыть issue