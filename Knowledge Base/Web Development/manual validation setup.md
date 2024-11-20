
```js
// _1. показывает error message
const showInputError = (formElement, inputElement, errorMessage) => {
  const errorElement = formElement.querySelector(`.${inputElement.id}-error`);
  // находим span in HTML в котором будет показываться тексе ошибки
  inputElement.classList.add('form__input_type_error');
  // цепляем на инпут класс ошибки - дает красную обводку
  errorElement.textContent = errorMessage;
  // цепляем к спану текст из браузерного validationMessage
  errorElement.classList.add('form__input-error_active');
  // делаем span видимым, цепляя на него класс активной ошибки
};

// _2. скрывает error message
const hideInputError = (formElement, inputElement) => {
  const errorElement = formElement.querySelector(`.${inputElement.id}-error`);
  inputElement.classList.remove('form__input_type_error');
  // снимаем класс ошибки с input field - становится не-красным
  errorElement.classList.remove('form__input-error_active');
  // снимаем класс ошибки со span - становится невидимым
  errorElement.textContent = '';
  // обнуляем текст спана
};

// _3. проверяет, все ли параметры валидности совпадают (их вроде 11), но в конечном итоге valid
// решает
const checkInputValidity = (formElement, inputElement) => {
  if (!inputElement.validity.valid) {
    // если параметр valid in inpEl.validity !== true;
    // то есть данное поле не валидно
    showInputError(formElement, inputElement, inputElement.validationMessage);
    // вызывает функц.1 - выбрасывает ошибку в текс и цвет рамки
  } else {
    hideInputError(formElement, inputElement);
  } // если все валидно - убирает классы ошибки с поля и span
};

// _4. проверяет все ли поля формы валидны. возвращает true если хотя-бы один invalid
const hasInvalidInput = (inputList) => inputList.some((inputElement) => !inputElement.validity.valid);

// _5. включает и выключает активность кнопки submit
const toggleButtonState = (inputList, buttonElement) => {
  // принимает на входе аррей инпутов и кнопку
  if (hasInvalidInput(inputList)) {
    buttonElement.classList.add('button_inactive');
    // если хоть одно поле не валидно - отключает кнопку
    // добавляя класс к ее элементу
  } else {
    buttonElement.classList.remove('button_inactive');
    // если все поля валидны - удаляет класс, включает кнопку
  }
};

// _6. массовое развешивание eventListeners
const setEventListeners = (formElement) => {
  // принимает форму
  const inputList = Array.from(formElement.querySelectorAll('.form__input'));
  // генерирует аррей(2) полей ввода
  const buttonElement = formElement.querySelector('.form__submit');
  // цепляет кнопку ввода
  toggleButtonState(inputList, buttonElement);
  // выключает кнопку, делая ее изначально не активной
  inputList.forEach((inputElement) => {
    // итерация через аррей(2)
    inputElement.addEventListener('input', () => {
      // на каждое поле вешается 'input' eventListener
      checkInputValidity(formElement, inputElement);
      // после этого проверяется валидность всех полей
      toggleButtonState(inputList, buttonElement);
      // в зависимости от предыдущего вкл/выкл активности кнопки
    });
  });
};

// _7. основная функция управляющая валидацией в масштабах страницы
const enableValidation = () => {
  const formList = Array.from(document.querySelectorAll('.form'));
  // генерирует аррей(1) всех форм в документе
  formList.forEach((formElement) => {
    // итерирует через аррей форм
    formElement.addEventListener('submit', (evt) => {
      // вешает 'submit' eventListener на каждую форму
      evt.preventDefault();
      // блокирует дефолтное поведение формы при сабмите
    });

    const fieldsetList = Array.from(formElement.querySelectorAll('.form__set'));
    // для каждой формы генерируется аррей филдсетов
    fieldsetList.forEach((fieldset) => {
      // для каждого филдсета генерируется аррей инпутов
      setEventListeners(fieldset);
      // в этом аррее запускается _6.setEvtLst - устанавливает eventLst
      // к каждому полю
    });
  });
};

enableValidation();
```