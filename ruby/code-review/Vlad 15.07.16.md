# Общие замечания
- Необходимо указывать версии/расположения в добавленных gemfile.
- Принято использовать RVM для управления версиями gem’ов.
- Удалить весь неиспользуемый код, файлы.

# Замечания по коду
- Валидацию в моделях удобнее писать более компактно.
  `validates :name, presence: true
	  validates :composition, presence: true
	  validates :price, presence: true`

  `validates :name, :composition, :price, presence: true`

- `Uploader` необходимо использовать свой для каждой из модели тогда image_uploader станет более читаемый.
- Сделать наследование и избежать в каждом контроллере указание модуля.
- Как правило при работе с `show/update/destroy` нам необходим конкретный объект: `@addition=Addition.find(params[:id])`. Чтобы избежать повторения кода необходимо вынести это в `before_action`.
- При использование gem `kaminari` дефолтные значения параметров можно задать в конфиге, проверка корректности осуществляется самим гемом и потребность в этих проверках отпадает.
- Убрать повторяющийся код `restaurants_controller.rb`.
- Можно вынести json во views с использованием `jbuilder`. Это правильно с точки зрения разработки т. к. `json` это аналог `html` — представление, и будет гораздо удобнее читаться.
- Также конкретно в этом случае можно объеденить контроллеры из `api/v1` и `dashboard`, используя `respond_to do |format| format.json` и `format.html`, т. к. в большинстве происходят одинаковые действия. Кол-во активного кода сократится в 2 раза.